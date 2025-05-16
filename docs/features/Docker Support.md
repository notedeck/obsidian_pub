---
created: 2025-05-17T00:55
updated: 2025-05-17T00:55
---
Quartz comes shipped with a Docker image that will allow you to preview your Quartz locally without installing Node.

You can run the below one-liner to run Quartz in Docker.

```sh
docker run --rm -itp 8080:8080 -p 3001:3001 -v ./content:/usr/src/app/content $(docker build -q .)
```
