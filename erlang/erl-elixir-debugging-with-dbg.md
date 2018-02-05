## Erlang/Elixir Debugging with dbg module

```
iex> pid = spawn(fn -> some_bad_fun() end)

iex> :dbg.tracer
{:ok, #PID<0.93.0>}

iex> :dbg.p(pid, [:call]) # tracing fn calls
{:ok, [{:matched, :nonode@nohost, 1}]}

iex> :dbg.tpl(:_, []); :timer.sleep(2_000); :dbg.stop()
```
