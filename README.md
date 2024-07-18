# Learning lunar.dev proxy

[lunar.dev](https://lunar.dev) is an egress proxy for API consumption management. The [Lunar Proxy](https://docs.lunar.dev/quick-start/#lunar-proxy-installation) is a container-based consumption gateway that manages an organization's outbound API traffic. 1-to-n [Lunar Interceptors](https://docs.lunar.dev/quick-start/#lunar-interceptor-installation)

## Authentication

Add the tenant name of your organization and lunar api key to `docker run` or the `devcontainer.json` which lunar.dev provided you

## Run the proxy

### with Docker

1. Start a container runtime e.g., colima, Docker Desktop, etc.
1. `docker run -d --rm -p 8000:8000 -p 8081:8081 -p 8040:8040 -e TENANT_NAME="ORGANIZATION CREATED DURING ACCOUNT SETUP" -e LUNAR_API_KEY="ISSUED BY LUNAR" -v $(pwd):/etc/lunar-proxy --name lunar-proxy lunarapi/lunar-proxy:latest`

> port 8000 is the default port when starting a Python web server so make sure one is not running to prevent a conflict `python3 -m http.server`

### as a dev container

> This does not work yet, and probably will never work since thd dev container appears to not have permissions
> to run as PID 1 to execute the /init script (the image's entrypoint)

1. Start a container runtime e.g., colima, Docker Desktop, etc.
1. Open VS Code, Cmd+Shift+P, Dev Containers: Open Folder in Container...

## Dev Container

Notice the `devcontainer.json` which specifies a lunar proxy container image, volume, ports and environment variables for the dev container.

## Resources

[lunar docs](https://docs.lunar.dev/)

[lunar git repo](https://github.com/TheLunarCompany/lunar)

[lunar control plane login](https://app.lunar.dev/)

[lunar dockerhub](https://hub.docker.com/r/lunarapi/lunar-proxy/tags)

[dev container spec](https://containers.dev/implementors/json_reference/)