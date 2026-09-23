# nightscout-go-systray

A Linux system tray app to display live Nightscout CGM data.

> Forked from [brettcodling/nightscout-go-systray](https://github.com/brettcodling/nightscout-go-systray) with bug fixes.

## Dependencies

```bash
sudo apt install libayatana-appindicator3-dev
```

## Install

```bash
git clone https://github.com/harmen91/nightscout-go-systray
cd nightscout-go-systray
go get -u ./...
go build .
mkdir -p ~/.local/bin
cp cgm ~/.local/bin/
```

## Ensure the binary exists and has execute permissions:

```bash
ls -la ~/.local/bin/cgm
chmod +x ~/.local/bin/cgm
```

## Usage

```
Usage of ./cgm:
  -url string
        Your nightscout url e.g. https://example.herokuapp.com
  -high float
        Your BG high target (default 8)
  -low float
        Your BG low target (default 4)
  -urgent-high float
        Your BG urgent high target (default 15)
```

Example:

```bash
cgm -url https://your-nightscout-url.com
```

## Create cgm.desktop and autostart on boot


```bash
mkdir -p ~/.config/autostart
nano ~/.config/autostart/cgm.desktop
```

Change username and https://your-nightscout-url.com accordingly

```ini
[Desktop Entry]
Type=Application
Name=Nightscout CGM
Exec=/home/username/.local/bin/cgm -url https://your-nightscout-url.com
Terminal=false
```
