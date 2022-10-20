# Traefik Docker Compose
## Prereqs
1. Docker with the compose plugin installed on the host
2. Cloudflare API token with DNS edit permissions to the zones used for ACME DNS verification.
## Config Steps
1. Clone this repo to the server.
2. Ensure the folders specified in the TRAEFIK_DATA_DIR and TRAEFIK_LOG_DIR variables exist.
3. In TRAEFIK_DATA_DIR, create an empty file named acme.json and set its permissions to 600.
4. In TRAEFIK_LOG_DIR, create empty files named traefik.log and access.log.
5. If using a host firewall, make sure TCP ports 80, 443, 8080, 8443, and 32400 are allowed.
6. In the cloned repo folder, create a file named .env and populate the environment variables specified below.
7. Run ```docker compose up -d```
## Environment Variables
**TRAEFIK_ACME_EMAIL**: Email address used for ACME/LetsEncrypt registration.
**TRAEFIK_API_URI**: The hostname that the Traefik dashboard should be accessible through. E.g. 'traefik.example.com'.
**TRAEFIK_ACME_CN**: Common name of the requested LetsEncrypt certificate. E.g. 'example.com'.
**TRAEFIK_ACME_SANS**: Comma-separated list of SANS (including wildcard SANS) to include in the LetsEncrypt certificate. E.g. '*.example.com,*.int.example.com'.
**TRAEFIK_DATA_DIR**: Path on the docker host to be mapped into the container for storing Traefik application data, i.e LetsEncrypt certs in acme.json.
**TRAEFIK_LOG_DIR**: Path on the docker host to be mapped into the container for storing Traefik access and application logs.
**TRAEFIK_CF_API_TOKEN**: Cloudflare API token with DNS edit permissions to the zone(s) specified in TRAEFIK_ACME_CN and TRAEFIK_ACME_SANS.

