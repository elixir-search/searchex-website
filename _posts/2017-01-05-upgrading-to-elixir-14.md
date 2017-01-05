---
title: Upgrading to Elixir 1.4
---

Yesterday Elixir 1.4 was [released][release]! Here are the 1.4 features that we used straight-away.

## Easier Escript Install

Elixir 1.3 introduced a one-liner command for installing escripts:

```
> mix escript.install https://raw.githubusercontent.com/elixir-search/searchex/master/searchex
```

The new command introduced in Elixir 1.4 is much better.

```
> mix escript.install hex searchex
```

Very slick!  Note that the escript is installed into `~/.mix/escripts` - make
sure it is on your path!

## Task.async_stream

Searchex intends to make heavy use of [GenStage][genstage] for concurrent
processing and backpressure.  GenStage is a bit complex, and I didn't have 
time to learn and use it in the first release.

Elixir 1.4 includes [Task.async_stream][tastream], an abstraction which
simplifies GenStage a great deal.  Here's at example from the Searchex code base:

```elixir
defp extract_docs(filescans) do
  filescans
  # this is the old implementation...
  # |> Enum.flat_map(fn(filescan) -> gen_docs(filescan) end)
  # the new code starts here...
  |> Task.async_stream(__MODULE__, :gen_docs, [])
  |> Enum.to_list   
  |> Enum.map(fn(el) -> elem(el, 1) end)
  |> List.flatten
end
```

With the old implementation, it took **25 seconds** to catalog a 400-document
collection.  With `Task.async_stream`, execution time is reduced to **10
seconds**. (quad-core i5)

Maybe the best part is seeing all cores running at max capacity.

![Concurrent Processing](/img/elixir_14/cpu_mon.png)

## Searchex 0.0.3

I just pushed Searchex 0.0.3 with these changes. 

[release]: http://elixir-lang.org/blog/2017/01/05/elixir-v1-4-0-released/
[genstage]: https://hexdocs.pm/gen_stage/Experimental.GenStage.html
[tastream]: https://hexdocs.pm/elixir/Task.html#async_stream/5


