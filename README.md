# Traefik Docker Compose
## Prereqs
* Docker with the compose plugin installed on the host
* Cloudflare API token with DNS edit permissions to the zones used for ACME DNS verification.
* If using a host firewall, make sure TCP ports 80, 443, 8080, 8443, and 32400 are allowed.
* NFS exports for storing Traefik logs and data
## Config Steps
1. Clone this repo to the server.
2. In the cloned repo folder, create a file named .env and populate the environment variables specified below.
3. Copy your Cloudflare API token into ./secrets/traefik-cf-dns-api-token.secret
4. Run ```docker compose up -d```
## Environment Variables
**TRAEFIK_ACME_EMAIL**: Email address used for ACME/LetsEncrypt registration.  
**TRAEFIK_API_URI**: The hostname that the Traefik dashboard should be accessible through. E.g. 'traefik.example.com'.  
**TRAEFIK_ACME_CN**: Common name of the requested LetsEncrypt certificate. E.g. 'example.com'.  
**TRAEFIK_ACME_SANS**: Comma-separated list of SANS (including wildcard SANS) to include in the LetsEncrypt certificate. E.g. '*.example.com,*.int.example.com'.  
**TRAEFIK_LOGS_NFS_SERVER**: IP or Hostname of the NFS server used for storing Traefik logs.
**TRAEFIK_LOGS_NFS_PATH**: Exported path on the NFS server for storing Traefik logs.
**TRAEFIK_DATA_NFS_SERVER**: IP or Hostname of the NFS server used for storing Traefik data.
**TRAEFIK_DATA_NFS_PATH**: Exported path on the NFS server used for storing Traefik data.

