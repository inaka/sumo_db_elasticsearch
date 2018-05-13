# sumo_db_elasticsearch

This is the [ElasticSearch](https://www.elastic.co/downloads/elasticsearch) adapter for [sumo_db](https://github.com/inaka/sumo_db)
tested with **2.2.0** version.


## ElasticSearch

### Install ElasticSearch

To install **ElasticSearch** please follow the instructions in this link:
[Installing ElasticSearch](https://www.elastic.co/guide/en/elasticsearch/reference/current/\_installation.html).


## Getting Started

To start use `sumo_db` with this ElasticSearch adapter `sumo_db_elasticsearch` is pretty easy, you only has to
follow these steps:

 1. Add `sumo_db` and `sumo_db_elasticsearch` as dependencies in your project.

Using **erlang.mk**:

```erlang
DEPS = sumo_db sumo_db_elasticsearch

dep_sumo_db               = git https://github.com/inaka/sumo_db.git               0.5.0
dep_sumo_db_elasticsearch = git https://github.com/inaka/sumo_db_elasticsearch.git 0.0.1
```

Using **Rebar**:

```erlang
{deps, [
  {sumo_db, {git, "https://github.com/inaka/sumo_db.git", {tag, "0.5.0"}}},
  {sumo_db_elasticsearch, {git, "https://github.com/inaka/sumo_db_elasticsearch.git", {tag, "0.0.1"}}}
]}.
```

 2. You need at least one doc/entity, let's use [sumo_test_people_elasticsearch](./test/sumo_test_people_elasticsearch.erl)
    as example.
    > NOTE: if you use this entity, you'll need to include `mixer` to the dependencies list

 3. Provide the configuration file, e.g.: [test.config](./tests/test.config).

 4. Now you can run your app and start using `sumo` from there.

### Running sumo from Erlang console

Start the Erlang console, adding the path to your beams and config file

    $ erl -pa ebin deps/*/ebin -config tests/test.config

Within the console:

```erlang
> application:ensure_all_started(sumo_db_elasticsearch).
10:16:55.730 [info] Application lager started on node nonode@nohost
10:16:55.740 [info] Application jiffy started on node nonode@nohost
10:16:55.759 [info] Application ranch started on node nonode@nohost
10:16:55.779 [info] Application crypto started on node nonode@nohost
10:16:55.779 [info] Application cowlib started on node nonode@nohost
10:16:55.824 [info] Application asn1 started on node nonode@nohost
10:16:55.825 [info] Application public_key started on node nonode@nohost
10:16:55.881 [info] Application ssl started on node nonode@nohost
10:16:55.893 [info] Application gun started on node nonode@nohost
10:16:55.901 [info] Application shotgun started on node nonode@nohost
10:16:55.909 [info] Creating wpool ETS table
10:16:55.909 [info] Application worker_pool started on node nonode@nohost
10:16:55.914 [info] Application tirerl started on node nonode@nohost
10:16:55.971 [info] Application sasl started on node nonode@nohost
10:16:55.994 [info] Application quickrand started on node nonode@nohost
10:16:55.995 [info] Application uuid started on node nonode@nohost
{ok,[syntax_tools,compiler,goldrush,lager,jiffy,ranch,
     crypto,cowlib,asn1,public_key,ssl,gun,shotgun,worker_pool,
     tirerl,sasl,quickrand,uuid,sumo_db,sumo_db_elasticsearch]}

% from here you can start using sumo

> sumo:find_all(sumo_test_people_elasticsearch).
[]
```


## Running Tests

```bash
make tests
```


## Contact Us

If you find any **bugs** or have a **problem** while using this library, please
[open an issue](https://github.com/inaka/sumo_db_elasticsearch/issues/new) in this repo (or a pull request :)).

And you can check all of our open-source projects at
[inaka.github.io](http://inaka.github.io)
