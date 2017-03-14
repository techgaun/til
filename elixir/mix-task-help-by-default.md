# Show help on mix task without args

Sometimes, on your mix tasks, you require certain arguments to be passed.
When they are missing, its often convenient to call the help for the mix task.

The snippet below should help in such cases:

```elixir
def run([]) do
  Mix.Tasks.Help.run(["db.cleanup"])
end

def run(args) do
  # your task logics
end
```
