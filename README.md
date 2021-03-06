# ironpeakservices/iron-nginx
Secure base image for running nginx.

`docker pull ghcr.io/ironpeakservices/iron-nginx:1.19.3`

## How is this different?
We build from the official nginx docker image, but additionally:
- an empty scratch container (no shell, unprivileged user, ...) for a tiny attack vector
- secure healthcheck binary for embedded container monitoring
- hardened nginx config
- hardened Docker Compose file
- max memory set to 1GB

## Example
```
FROM ghcr.io/ironpeakservices/iron-nginx:1.19.3
COPY --chown=nonroot css/ js/ html/ /assets
```

## Update policy
Updates to the official nginx docker image are automatically created as a pull request and trigger linting & a docker build.
When those checks complete without errors, a merge into master will trigger a deploy with the same nginx version to packages.
