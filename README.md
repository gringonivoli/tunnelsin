# TunnelsIn

A simple command-line tool to create instant secure tunnels to your localhost services using either Cloudflared or Serveo.

## Overview

TunnelsIn makes it easy to expose your local web servers to the internet through secure tunnels. This is useful for:

- Sharing your work with clients or colleagues
- Testing webhooks
- Demoing applications without deployment
- Accessing your local development environment from other devices

## Requirements

- Bash shell
- For Cloudflared tunnels: [Cloudflared CLI](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/install-and-setup/installation/) installed
- For Serveo tunnels: SSH client installed

## Installation

1. Clone this repository or download the `tunnelsin` script
2. Make the script executable:
   ```
   chmod +x tunnelsin
   ```
3. Optionally, move it to a directory in your PATH for easier access

## Usage

```bash
./tunnelsin [service] [port1] [port2] ...
```

Where:
- `service` is either `cloudflared` or `serveo`
- `port1`, `port2`, etc. are the local ports you want to expose

### Examples

Create a Cloudflared tunnel to a local server running on port 3000:
```bash
./tunnelsin cloudflared 3000
```

Create Serveo tunnels to multiple local servers:
```bash
./tunnelsin serveo 3000 8080 5000
```

## Features

- Creates tunnels using either Cloudflared or Serveo
- Supports multiple tunnels simultaneously
- Displays tunnel URLs for easy access
- Automatically cleans up tunnels on exit

## How It Works

The script establishes secure tunnels using either:

1. **Cloudflared**: Creates quick tunnels using Cloudflare's Argo Tunnel service
2. **Serveo**: Uses SSH reverse tunneling to expose local ports

When the script runs, it will display the public URLs that point to your local services.

## Troubleshooting

- Check the output files (`cloudflared_PORT_output.txt` or `serveo_PORT_output.txt`) for detailed logs
- Ensure the required services (Cloudflared or SSH) are installed and accessible
- Verify that the local ports you're trying to expose have active services running

## License

MIT
