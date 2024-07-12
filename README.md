# dockerized_github_runner

## Create a new fine-grained GH token
The token required needs _"Self-hosted runners" organization permissions (write)_ permissions to your organization. The token will be used to generate a second token that is actually used to register the runner. This setup allows to scale the system, as arbitrary many runner-tokens can be generated. 

## Decide on configuration
The runner can be configured with the following values
### Convenience variables
| Environment Variable | Description                    |
|----------------------|--------------------------------|
| `RUNNER_LABELS`      | Labels for the GitHub runner   |

### Technical variables
| Environment Variable | Description                    |
|----------------------|--------------------------------|
| `GITHUB_ORG`         | GitHub organization name       |
| `GITHUB_TOKEN`       | Token for GitHub authentication|

All those environment variables must be set!

## Startup using Docker
After building the image using
```
docker build --name github_runner .
```
you can start it using
```
docker run --rm --name github_runner
 -e RUNNER_LABELS=<custom tag>
 -e GITHUB_ORG=<organization name>
 -e GITHUB_TOKEN=<token>
 github_runner
```

## Credits
Adapted from https://github.com/marcel-dempers/docker-development-youtube-series