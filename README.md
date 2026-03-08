# vpssnitch

because your VPS needs a snitch, and I'm too paranoid to trust it alone.

## what the hell is this

I built this monstrosity because my servers kept bleeding resources like a toxic relationship, and I was tired of waking up to "your potato is on fire" emails. It's a Bash script that snitches on your VPS in real-time - CPU, RAM, disk, network spikes, Docker containers, the works. It graphs everything with sparklines because I thought it looked cool, and throws in some childish humor because adulting is hard.

Runs in your terminal, logs to a file, and alerts you when things get spicy. Daemon mode for systemd if you're into that masochism.

## installation (don't screw this up)

1. Clone this repo: `git clone https://github.com/kisalnelaka/vpssnitch.git`
2. Make it executable: `chmod +x vpssnitch`
3. Run it: `./vpssnitch`

That's it. No dependencies beyond basic Linux utils. If you're on Windows, go cry in a corner.

## usage (because reading is hard)

```
./vpssnitch [interface] [options]
```

### options

- `--daemon`: Run in daemon mode (no screen clearing, for systemd)
- `--no-clear`: Don't clear the terminal (for logging or whatever)
- `--interval N`: Refresh every N seconds (default 2, because I'm impatient)
- `--log-file PATH`: Where to dump the logs (default ~/.local/share/vpssnitch/vpssnitch.log)
- `--quiet`: Less jokes, less alerts (for the boring people)
- `--help`: This, but you already know

### examples

Watch your main interface:
```
./vpssnitch
```

Specify interface:
```
./vpssnitch eth0
```

Daemon mode with custom interval:
```
./vpssnitch --daemon --interval 5
```

Log to custom file:
```
./vpssnitch ens3 --log-file /var/log/my-snitch.log
```

## what it shows

- Hostname, uptime, load average
- CPU usage with progress bar and sparkline
- RAM and swap with progress bars
- Disk usage for root
- Network RX/TX rates, detects spikes
- Top CPU and memory processes
- Docker status if available
- A random snarky comment each refresh

Alerts when CPU >90%, RAM >80%, or network spikes. Logs everything to a file.

## why I made this

Because monitoring tools are either enterprise bloat or nonexistent. I needed something lightweight that doesn't require a PhD to set up. Also, caffeine withdrawal.

## license

MIT, because sharing is caring, and I don't want to deal with lawyers.

## disclaimer

This is code I wrote while dissociating. It works suspiciously well, but if your server explodes, that's on you. Test it first, you goldfish.