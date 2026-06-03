# MarketLab

MarketLab is a fake-money prediction market app for the Cursor workshop.

## Setup

Open this repo in Cursor and run the setup command for your operating system.

### macOS / Linux

```bash
bash ./scripts/unix-setup.sh
```

### Windows

```powershell
pwsh -ExecutionPolicy Bypass -File .\scripts\windows-setup.ps1
```

If `pwsh` is not available:

```powershell
powershell -ExecutionPolicy Bypass -File .\scripts\windows-setup.ps1
```

After setup finishes, open a new Cursor terminal.

## Run

```bash
task dev
```

Open [http://localhost:3000](http://localhost:3000).
