# Containerization Templates

To help maintain an official FIWARE clone of container images, some additional files may need to be added to the GitHub
Actions as shown:

```text
.github
├── fiware
│   └── config.json
└── workflows
    ├── fiware-sync-to-upstream.yml
    ├── fiware-release.yml
    └── fiware-enterprise.yml
```

The `fiware/config.json` file **MUST** be present and hold sufficient information to allow a build to be pushed to the
FIWARE Foundation's container registries (currently Docker Hub and GHCR)

```json
{
    "enabler": "Orion-LD Context Broker",
    "chapter": "core",
    "academy": "/core/orion-ld",
    "readthedocs": "fiware-orion-ld",
    "helpdesk": "Orion-LD",
    "coverall": "",
    "github": ["FIWARE/context.Orion-LD"],
    "dockerbuild": "../build.sh",
    "dockerregistry": ["hub.docker.com"],
    "docker": ["fiware/orion-ld"],
    "email": "ken.zangelin@fiware.org",
    "status": "incubating",
    "compose": "https://raw.githubusercontent.com/FIWARE/context.Orion-LD/develop/docker/docker-compose.yml",
    "exclude": ["mongo"],
    "stackexchange": ["http://stackoverflow.com/questions/tagged/fiware-orion"],
    "unit-test": "XXXXX",
    "smoke-test": "XXXXX",
    "dockerfile": "XXXXX"
}
```

Either a location of a docker registry must be present, or sufficient information available in the `dockerbuild` file
(given as a relative path) to enable a total rebuild of a location.

Docker Automated Builds are no longer free for all users, contributors may use GitHub Actions to push to the container
registry of their choice, an example pushing to both Docker Hub and GCHR can be found
[here](https://github.com/FIWARE/iotagent-isoxml/tree/master/.github/workflows) Contributors may also continue to use
Docker Automated Builds if they wish.

Contributors should include a docker-compose to allow for smoke testing.

If build actions are scheduled to run from FIWARE clones only, the relevant Job can be annoated as shown below:

```yaml
jobs:
    deploy:
        runs-on: ubuntu-18.04
        if: ${{ github.repository_owner == 'FIWARE' }}
        steps:
```
