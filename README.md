# CTF-Tutorial

# rogueap-detector — Setup Guide

## 1. Get the files

Go to the repo on GitHub and either clone it or download each file individually:

```bash
git clone https://github.com/Huwaba/CTF-Tutorial/ rogueap-detector
cd rogueap-detector
```

(Or if you're copying files manually instead of cloning: open `config.sh` on GitHub, copy its contents, and paste into a new local file with the same name — repeat for `scripts/detect.py`, `start.sh`, and `stop.sh`.)

## 2. Verify the files are present

```bash
ls -la
ls -la scripts/
```

You should see `config.sh`, `start.sh`, `stop.sh`, and `scripts/detect.py`.

## 3. Make the scripts executable

```bash
chmod +x start.sh stop.sh config.sh scripts/*.py
```

## 4. Install dependencies

```bash
sudo apt update
sudo apt install -y aircrack-ng python3-scapy
```

## 5. Run `start.sh`

```bash
sudo ./start.sh
```

This brings your interface into monitor mode and begins hopping channels, watching for the rogue SSID (`AirOrangeX`) defined in `config.sh`.

## 6. Stop it with `stop.sh`

```
Ctrl+C
```

or, if it's left in a bad state:

```bash
sudo ./stop.sh
```

## Notes

- `config.sh` holds all the settings (interface name, channels, watched SSID) — edit that file if you need to change any of them, no need to touch `detect.py`.
- Logs are written to `logs/detector.log` if you want to review alerts after a run.
