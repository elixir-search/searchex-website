---
title: Hello World
---

Over the past few weeks I made the first commits for Searchex, a full-text
search engine written in pure Elixir.  

## Technical Potential

Full-text search really benefits from concurrent processing.  Elixir is the
best platform I've seen for concurrent, fault-tolerant apps.  And there's been
recent Elixir developments that are ideally suited for distributed search.
[GenStage](http://elixir-lang.org/blog/2016/07/14/announcing-genstage) /
[Flow](http://www.slideshare.net/Elixir-Meetup/experimentalflow-yurii-bodarev)
is one.  Another is the Phoenix work on [CRDTs and
Presence](https://dockyard.com/blog/2016/03/25/what-makes-phoenix-presence-special-sneak-peek),
and potential application for process discovery.  [Phoenix
Channels](http://www.phoenixframework.org/docs/channels) have great potential
for easily connecting I/O streams to a search engine.

Elixir can be an amazing platform for a search engine.

## Simplify and Streamline

Elixir has the potential to reduce the number of components in the production
stack.  Adrian Philipp highlighted this benefit in a [recent
article](http://adrian-philipp.com/post/why-elixir-has-great-potential).

<img src="/img/hello_world/stack.jpg" width="75%" alt="Erlang Technology Comparison">

Note that this chart does not include a line-item for a Search Engine!  The Elixir
developer still needs to use an External search engine (like ElasticSearch).  

The external dependency requires extra labor and handholding.
Installing/configuring the service, designing/building/tuning the integration,
monitoring and managing in production.  Yuck!

This [blog post](http://teamon.eu/2016/tuning-elixir-genstage-flow-pipeline-processing)
from Tymon Tobloski describes his efforts to integrate Elastic Search.  The
custom integration and tuning looks like a lot of work!

With Searchex I'm certain we can simplify and streamline a great deal.

## A New Project

I expect Searchex to be useful for the Elixir community and to be a great
showcase for the Beam and GenStage.  I'm looking for collaborators and mentors.
Let me know if you're interested in getting involved!

