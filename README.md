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
cd nightscout-go-systray/nightscout-go-systray
go get -u ./...
go build .
cp cgm ~/.local/bin/
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

## Run in background

To run without a terminal, create a systemd user service:

```bash
mkdir -p ~/.config/systemd/user
cat > ~/.config/systemd/user/cgm.service << EOF
[Unit]
Description=Nightscout CGM systray

[Service]
ExecStart=/home/$USER/.local/bin/cgm -url https://your-nightscout-url.com
Restart=on-failure

[Install]
WantedBy=default.target
EOF

systemctl --user enable cgm
systemctl --user start cgm
```

Check status:

```bash
systemctl --user status cgm
```

