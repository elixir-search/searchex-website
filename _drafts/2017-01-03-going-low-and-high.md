---
title: Go Low or High?
---

In the [last post][v001], we explained that the Searchex architecture is
designed to be composable and to accomodate change.

Here we discuss Searchex positioning, along with some potential guidelines for
setting development priorities.

## The Strengths of Elixir

Somewhat paradoxically, Elixir has unique strengths at both the low-end and the
high-end.  

On the low end, Elixir runs awesome on small devices and embedded systems.
In my eyes, the [Nerves Project][nerves] is a kind of technical miracle.

On the high end, the example of [WhatsApp](http://whatsapp.com) shows that
Elixir / Erlang has world-class scalability.

## Search Alternatives

In Search, the most commonly used solution today is something like Elastic
Search.  As explained in the [Hello World][hello] post, the core value
proposition for Searchex is to simplify and streamline by eliminating external
dependencies like Elastic Search.

Beyond that, I believe Searchex has unique opportunities at both the low-end and
the high-end.

## Low-End Search

Today on the low-end we have grep (and grep-like utilities).  Grep has proven
its value, but there are use-cases not easily handled:

1. multiple documents in one file
2. filtering by document meta-data
3. relevance-ranked search results
4. returning the matched document, not just the regex hits
5. remote documents
6. data streams

A "grep-plus" command-line tool could be useful for a range of low-end search
jobs:

- social media filtering and alerting
- elixir tooling: hex-docs, package descriptions
- vim and emacs plugins
- multi-source searching: local filesystem plus internet services 

## High-End Search

When it comes to high-end search, there is so much to say.  Distributed search,
real-time filtering, large-scale data analytics, much much more.  To reach the
highest levels of performance we'll need a hybrid solution with Elixir driving
Rust or C based NIFs.

At this time, all I want to say about High-End Search is that I have faith that
Elixir is going to get the job done better than any other platform I see.  And
that it will be a lot of work to get there.

## Approach

I think these ought to be the development priorities:

1. build an integrated Ecto plugin, so that full-text search from a Phoenix
   project is a no-brainer
2. find opportunities to solve low-end search problems with a simple CLI, so
   that Searchex becomes commonly used by Elixir developers
3. worry about high-end search somewhere down the road

Over the next few weeks I'll be asking folks for their feedback.  Let us know
what you think in the comments below!



[roadmap]: https://github.com/elixir-search/searchex#roadmap
[nerves]:  http://nerves-project.org/
[hello]:   {% post_url 2016-12-28-hello-world %}
[v001]:    {% post_url 2017-01-01-searchex-v0_0_1 %}

