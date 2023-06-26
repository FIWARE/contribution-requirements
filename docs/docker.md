## Requirements for Containerization (Docker/Quay.io)

This page summarizes Requirements for providing Container Images for FIWARE Generic Enablers.
[Click here](https://docs.docker.com/engine/understanding-docker/) for an introduction to Docker. Container Images can
be hosted on any publicly available container registry (e.g. `hub.docker.com`, `ghcr.io`, `quay.io`)

### General Requirements

<span style="color:#233c68;">&#x24D5;</span> At least one Dockerfile (hereby named as 'reference Dockerfile'), intended
to FIWARE Generic Enabler users, **MUST** be provided.

The base image (Ubuntu, CentOS, etc.) for such a Dockerfile might depend on each FIWARE Generic Enabler, although some
recommendations (see below) are provided. The Dockerfile can be at the root folder of the FIWARE Generic Enabler's
Repository or under a folder named `docker`. Additional Hacker-orientated Dockerfiles **MAY** be provided as well.

<span style="color:#233c68;">&#x24D5;</span> Each Docker image **SHOULD** define the following tags (present at
[DockerHub](https://hub.docker.com/) or an alternative public container registry):

-   `latest`: **On the FIWARE Generic Enabler owner's account** will correspond to the latest build (latest code
    snapshot) of the FIWARE Generic Enabler. It might not be stable.

-   `<release n>`: one tag per relevant and active stable release. The name of the tag will correspond to the name
    assigned to the release in GitHub.

-   `FIWARE_<release n>`: one stable release for all FIWARE components. This indicates FIWARE Generic Enablers which
    will work together.

<span style="color:#233c68;">&#x24D5;</span> The reference Dockerfile **SHOULD** be present under a separate `docker`
folder of the GE repository.

<span style="color:#233c68;">&#x24D5;</span> The relative path to the reference Dockerfile **SHOULD** be present in a
[Docker Template](./docker_templates) placed in the following location with the `.github/fiware/config.json`. The
template file **MUST** hold sufficient information to allow for the FIWARE Foundation to clone or rebuild images:

-   A basic image clone requires that the `dockerregistry` and `docker` image name are known
-   An image rebuild requires that the relative path to a build script is present
-   An integration test requires that the relative path to a test script is present
-   An integration test with dependencies requires that the relative path to a `docker-compose` file is present

The level of test and rebuild compliance will vary dependent upon the maturity of the product. More details can be found
under [Docker Templates](./docker_templates)

<span style="color:#233c68;">&#x24D5;</span> Should your FIWARE Generic Enabler depend on other components (Databases,
etc.) you **MUST** provide a `docker-compose.yml` file that will allow to instantiate the GE together with its
dependencies.

<span style="color:#233c68;">&#x24D5;</span> The GitHub repository `README.md` **MUST** have a Docker reference - this
is a link on the mandatory Docker Pulls `README.md` badge.

<span style="color:#233c68;">&#x24D5;</span> The **Read the Docs** Installation Documentation **MUST** include
references to the Docker Hub image, and how to configure it

### Building Docker Images

<span style="color:#233c68;">&#x24D5;</span> There **MUST** be a container image  specific `README` for the Docker Hub/Quay.io image
documentation. This lies in the same directory as the `Dockerfile` and **SHOULD not** be a copy of the root GitHub
`README.md` since the required information is not the same.

<span style="color:#233c68;">&#x24D5;</span> The container image `README.md` **MUST** list or link to the documentation holding
all available `ENV` variables that can be supplied to the Docker Image and a reasonable definition of each of them.

<span style="color:#233c68;">&#x24D5;</span> The container image `README.md` **MUST** give complete instructions about how to
work with the corresponding Docker container. Bear in mind that a copy of this `README.md` should also be included as
documentation directly on the public container registry used to hold the image.

<span style="color:#233c68;">&#x24D5;</span> Where configuration occurs via a `config` file, and the image cannot be
driven by `ENV` variables, a sample `config` file **SHOULD** be supplied and injected as part of the Docker build.
Reference Dockerfiles **SHOULD NOT** `COPY .` default configuration directly from GitHub.

<span style="color:#233c68;">&#x24D5;</span> The reference `Dockerfile` **SHOULD** be split into Multiple Stages:

This is good practice to reduce the size of the layers. Although the names of the stages are not that important it is
easier to align with a common naming convention. The following common names for build stages are recommended and **MAY**
be used:

-   `init` - Gather Sources
-   `builder` - Build Sources
-   `distroless` - “Distroless” Build (where supported)
-   `node-slim` etc. - where a build stage aligns to a Docker
    [official Image](https://docs.docker.com/docker-hub/official_images/) use that as the name of the stage.

Note that the main supported distro build must be the last one in the file as it will be the default.

<span style="color:#233c68;">&#x24D5;</span> Flexible base images **SHOULD** be supported using
[build-args](https://vsupalov.com/docker-arg-env-variable-guide/), an example can be seen below:

```bash
docker build -t rhel-build  \
  --build-arg DISTRO=registry.access.redhat.com/ubi7/nodejs-12 \
  --build-arg NODE_VERSION=12 \
  --build-arg BUILDER=registry.access.redhat.com/ubi7/ubi \
  --build-arg PACKAGE_MANAGER=yum \
  --no-cache \
  .
```

The following names for build arguments are recommended and **MAY** be used:

-   `BUILDER` - baseline Docker image for creating sources
-   `DISTRO` - baseline Docker image for default build
-   `DISTROLESS` - baseline Docker image for “distroless” build
-   `PACKAGE_MANAGER` - name of package manager to use `yum`, `apt`, `apk` etc.
-   `<NODE>_VERSION` - Supported Version ( plus equivalents for Python, Java etc.)
-   `GITHUB_ACCOUNT` - GE Owner account on GitHub
-   `GITHUB_REPOSITORY` - Name of the source code repository on GitHub
-   `DOWNLOAD` - e.g. by GitHash or tag version
-   `SOURCE_BRANCH` - e.g. `master`

<span style="color:#233c68;">&#x24D5;</span> Where flexible base images are available, the `README` **MUST** state how
to build them and which build options are officially supported by the GE Owner.

### Running Container Images

<span style="color:#233c68;">&#x24D5;</span> If the reference `Dockerfile` hides sensitive information (e.g. passwords)
using Docker Secrets, the `README.md` **MUST** list all available `ENV` variables which have an equivalent `_FILE` that
can be supplied by secrets.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#no_leaked_credentials">&#x24D2;</a>
It **MUST** be possible to supply sensitive information using the Docker Secrets mechanism as well as plain text
variables for testing. Sensitive information (e.g. passwords) **MUST NOT** be passed in plain text - `ENV` variables
alone.

<span style="color:#233c68;">&#x24D5;</span> It **SHOULD** be possible to configure the FIWARE Generic Enabler config
entirely through - `ENV` variables. Where this is not possible, the `README.md` **SHOULD** explain how to mount a volume
to set the configuration.

### Publication Requirements

<span style="color:#233c68;">&#x24D5;</span> The FIWARE Generic Enabler owner will be responsible for Docker publication
and maintenance operations. Docker builds **SHOULD** be automated. FIWARE Generic Enabler Owner's build should be
triggered by `git push`, FIWARE's one will be triggered by new tagged releases.

<span style="color:#233c68;">&#x24D5;</span> Container Images **MUST** be tested before being published to the
community. Error in Docker materials of a FIWARE Generic Enabler will be considered as critical and **MUST** be fixed
immediately.

<span style="color:#233c68;">&#x24D5;</span> Maintenance and release of interim point releases **MUST** be done using
the FIWARE Generic Enabler Owner own contributor account.

<span style="color:#233c68;">&#x24D5;</span> A bash script **MUST** be added so that under `.github/fiware/image-clone.sh` so that the FIWARE Infrastructure is informed
whenever a release version is tagged.

```
set -e

SOURCE="telefonicaiot/fiware-orion"

DOCKER_TARGET="fiware/$(basename $(git rev-parse --show-toplevel))"
QUAY_TARGET="quay.io/fiware/$(basename $(git rev-parse --show-toplevel))"
VERSION=$(git describe --tags $(git rev-list --tags --max-count=1))

docker pull -q "$SOURCE":"$VERSION"

for i in "$@" ; do
    if [[ $i == "docker" ]]; then
        echo 'cloning from '"$SOURCE $VERSION"' to '"$DOCKER_TARGET"
        docker tag "$SOURCE":"$VERSION" "$DOCKER_TARGET":"$VERSION"
        docker tag "$SOURCE":"$VERSION" "$DOCKER_TARGET":latest
        docker push -q "$DOCKER_TARGET":"$VERSION"
        docker push -q "$DOCKER_TARGET":latest
    fi
    if [[ $i == "quay" ]]; then
        echo 'cloning from '"$SOURCE" "$VERSION"' to '"$QUAY_TARGET"
        docker tag "$SOURCE":"$VERSION" "$QUAY_TARGET":"$VERSION"
        docker tag "$SOURCE":"$VERSION" "$QUAY_TARGET":latest
        docker push -q "$QUAY_TARGET":"$VERSION"
        docker push -q "$QUAY_TARGET":latest
    fi
done

```

<span style="color:#233c68;">&#x24D5;</span> Builds of components which do not successfully integrate with
`/repository/fiware/orion/latest` will not be added to the FIWARE account. When changes have been made, a
[SemVer](https://semver.org/) release on the source code will be required in order to complete the release. This will
kick off the FIWARE build. Obviously, it is essential that such a build passes the mandatory integration tests.

### Recommended best practices

<span style="color:#233c68;">&#x24D5;</span> Dockerfiles **SHOULD** follow best practices as described
[here](https://docs.docker.com/articles/dockerfile_best-practices/)

<span style="color:#233c68;">&#x24D5;</span> Dockerfiles **SHOULD** be based on the latest LTS (Long Term Support)
release of the base image - e.g. `ubuntu:22.04`, `node:18`, etc.

<span style="color:#233c68;">&#x24D5;</span> Although default values **SHOULD** be defined, exposed ports **MUST NOT**
be fixed, and **MUST** be configurable using `ENV` variables.

Dockerfiles should be publicly available, and therefore can be read by outside developers and can reflect on the quality
of the product in question. Although image size is not everything, there are several ways to reduce the bloat of docker
images and good practice should be followed:

-   Where possible, base the image on `debian:9-slim` rather than `Ubuntu`.

-   Node-based images should use `node-galium-slim` where possible (which is also debian-based).

-   Builds should not package development dependencies and should remove unnecessary tools such as `wget`, `curl`, and
    so on - if necessary load these tools and remove them within the same layer.

-   Use the `RUN git clone` method of obtaining source code instead of `ADD/COPY` in case source code can be deleted.

-   Consider adding build-args to be able to download latest/stable/specific release of the codebase.

-   Additional alpine-based builds may be requested for some components.

### Label description content

<span style="color:#233c68;">&#x24D5;</span> Dockerfiles **SHOULD** put the following static common
[Open Container Initiative](https://opencontainers.org/) labels inside the Dockerfile:

| Name                                     | Description                                    | Example                                                                                                                                                                                                      |
| ---------------------------------------- | ---------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `org.opencontainers.image.authors`       | Email addresses of responsible contacts        | `iot_support@tid.es`                                                                                                                                                                                         |
| `org.opencontainers.image.description`   | Description of the component                   | _An Internet of Things Agent for the Ultralight 2.0 protocol (with AMQP, HTTP and MQTT transports). This IoT Agent is designed to be a bridge betweenUltralight and the NGSI interface of a context broker._ |
| `org.opencontainers.image.documentation` | Link to the documentation                      | `https://fiware-iotagent-ul.rtfd.io/`                                                                                                                                                                        |
| `org.opencontainers.image.licenses`      | The license type                               | _AGPL-3.0-only_                                                                                                                                                                                              |
| `org.opencontainers.image.revision`      | The GitHash or branch the image was built from | `d0698fad9a0880edcbdf2cc23ba775d81c3f51c1`                                                                                                                                                                   |
| `org.opencontainers.image.source`        | Location where the source code can be found.   | `https://github.com/telefonicaid/iotagent-ul`                                                                                                                                                                |
| `org.opencontainers.image.title`         | The title of the image                         | _IoT Agent for the Ultralight 2.0 protocol_                                                                                                                                                                  |
| `org.opencontainers.image.vendor`        | The name of the caretaker organization.        | _Telefónica Investigación y Desarrollo, S.A.U_                                                                                                                                                               |

An example of Static Labels can be found in
[this `Dockerfile`](https://github.com/telefonicaid/iotagent-ul/blob/master/docker/Dockerfile#L199-L207)

<span style="color:#233c68;">&#x24D5;</span> Dockerfiles **SHOULD** also add the following dynamic labels inside the
Dockerfile:

| Name                               | Description                         | Example      |
| ---------------------------------- | ----------------------------------- | ------------ |
| `org.opencontainers.image.created` | The date the image was built.       | `2020-10-20` |
| `org.opencontainers.image.version` | The SemVer release of the component | `1.15.0`     |

An example of Dynamic Labelling can be found in
[this Build Hook](https://github.com/telefonicaid/iotagent-ul/blob/master/docker/hooks/build#L23-L27)

<span style="color:#233c68;">&#x24D5;</span> For the automation of security alerts, Dockerfiles **SHOULD** put the
following additional FIWARE related labels inside the Dockerfile:

| Name                           | Description                                                                                                                 | Example                    |
| ------------------------------ | --------------------------------------------------------------------------------------------------------------------------- | -------------------------- |
| `org.fiware.contact.localpart` | A comma separated [partial email addresses](https://en.wikipedia.org/wiki/Email_address#Local-part) of responsible contacts | `fernando.lopez,jason.fox` |
| `org.fiware.contact.domain`    | An email server [domain name](https://en.wikipedia.org/wiki/Email_address#Domain) of responsible contacts                   | `fiware.org`               |

Note that the Dockerfile `MAINTAINER` instruction is deprecated. The `LABEL maintainer` instruction is a much more
flexible version of this and you should use it instead, as it enables setting any metadata you require, and can be
viewed easily, for example with `docker inspect`. See section [Label description content](#label-description-content)
for more details.

Note that Image labels can be read using the `docker inspect` command:

```bash
docker inspect --format '{{json .Config.Labels}}' test | jq .
```

## Examples

-   [GitHub Repository](https://github.com/telefonicaid/fiware-orion/tree/master/docker)

-   [Docker Hub repository](https://hub.docker.com/r/fiware/orion/)

## Support

Should you have any question please send an email to [fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org)
