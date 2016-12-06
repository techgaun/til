# Turn Elixir code to erlang code

This one was shared in #til of [elixir-lang slack](https://elixir-lang.slack.com/messages/til/). Not sure how I can apply it to be useful but kinda cool.

```elixir
defmodule A do
  def a, do: IO.puts "I am A"
end
```

```elixir
iex(1)> c("a.ex")

iex(2)> {:ok , {_, [{:abstract_code, {_, ast}}]}} = :beam_lib.chunks('Elixir.A.beam', [:abstract_code])

iex(3)> IO.puts :erl_prettypr.format(:erl_syntax.form_list(ast))
```
