Chatty
======

A basic IRC client that is most useful for writing a bot.


## Installation

Add Chatty as a dependency to your Mix project:

```elixir
def application do
  [applications: [:chatty]]
end

defp deps do
  [{:chatty, github: "alco/chatty"}]
end
```


## Usage

You need to set the following environment paramters for the `:chatty` app:

  * `:nickname` – the nick to use when connecting and identifying with NickServ
  * `:channels` – a list of channel names to join upon connect
  * `:password` (optional) – when set, Chatty will identify with NickServ using
    this password
  * `:logging_enabled` (optional) – whether to print connection info to the
    output; off by default

Chatty's behaviour is customized by means of adding hooks that get invoked on
each incoming message. A ping hook is included as an example, try out like
this:

```iex
iex -S mix

iex> Chatty.add_hook :ping, &Chatty.Hooks.PingHook.run/2, in: :text, direct: true
:ok
```

Now, whenever Chatty sees the message `<nickname>: ping`, it will send one of
predefined replies back to the sender:

```
02:05:35      @true_droid | beamie_test: ping
02:05:35      beamie_test | true_droid: spank
```


## License

This software is licensed under [the MIT license](LICENSE).
