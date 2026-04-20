## Cloudflare DDNS Updater

This addon is used to update DDNS records on Cloudflare.

## Requirements
* A Cloudflare account
* A domain name setup to use Cloudflare as the DNS provider

## Configuration

```yaml
ddns_protocol: both
check_interval: 300
retry_interval: 60
config:
  - zone: example.com
    token: <token from cloudflare>
    domains: my.example.com,www.example.com
  - zone: acme.com
    token: <token from cloudflare>
    domains: my.acme.com,www.acme.com
```

### `ddns_protocol`
Controls which IP protocol(s) the add-on updates:

- `ipv4 only`
- `ipv6 only`
- `both`

### `check_interval`
How often (in seconds) the add-on checks whether Cloudflare records need to be updated.

### `retry_interval`
How long (in seconds) ddclient waits before retrying after a failed update.

## Token

The token is an Account API token from Cloudflare.

The token is created under Manage Account -> Account API Tokens -> Create Token

It must have the permissions:
 - Zone - DNS - Edit
 - Zone - Zone - Read
 - The Zone resources must be "Include - All" (or your specific account)

## How it works

The addon checks the configured public IP protocol(s) and updates the DDNS records for the domains in the configuration.
