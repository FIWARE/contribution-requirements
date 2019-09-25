## Requirements for GE Dockerization (Containerization)

This page summarizes Requirements for providing Docker Containers for FIWARE
GEs. [Click here](https://docs.docker.com/engine/understanding-docker/) for an
introduction to Docker.

## General Requirements

-   At least one Dockerfile (hereby named as 'reference Dockerfile'), intended
    to GE users, **MUST** be provided. The base image (Ubuntu, CentOS, etc.) for
    such a Dockerfile might depend on each GE, although some recommendations
    (see below) are provided. The Dockerfile can be at the root folder of the
    GE's Repository or under a folder named `docker`.

-   Hacker-oriented, i.e. for GE development, Dockerfiles **MAY** be provided as
    well.

-   Each Docker image **SHOULD** define the following tags (present at
    [Dockerhub](https://hub.docker.com/)):

    -   `latest`: **On the GE owner's account** will correspond to the latest
        build (latest code snapshot) of the GE. It might not be stable.
    -   `<release n>`: one tag per relevant and active stable release. The name
        of the tag will correspond to the name assigned to the release in
        GitHub.
    -   `FIWARE_<release n>`: one stable release for all FIWARE components. This
        indicates GEs which will work together.

-   The reference Dockerfile **MAY** be present under a separate `docker` folder
    of the GE repository

-   Should your GE depend on other components (Databases, etc.) you **MUST**
    provide a `docker-compose.yml` file that will allow to instantiate the GE
    together with its dependencies.

-   There **MUST** be a docker-hub specific README for the docker image
    documentation. This lies in the same directory as the `Dockerfile` and
    **SHOULD not** be a copy of the root GitHub `README.md` since the required
    information is not the same.

-   The Docker `README.md` **MUST** give complete instructions about how to work
    with the corresponding Docker container. Please bear in mind that such a
    `README.md` will also be included as part of the Dockerhub documentation.

-   The Docker `README.md` **MUST** list or link to the documentation holding
    all available `ENV` variables that can be supplied to the Docker Image

-   If the Docker file hides sensitive information (e.g. passwords) using Docker
    Secrets, the `README.md` **MUST** list all available `ENV` variables which
    have an equivalent `_FILE` that can be supplied by secrets.

-   It **MUST** be possible to supply sensitive information using the Docker
    Secrets mechanism as well as plain text variables for testing. Sensitive
    information (e.g. passwords) **MUST NOT** be passed in plain text - `ENV`
    variables alone.

-   It **SHOULD** be possible to configure the GE config entirely through -
    `ENV` variables. Where this is not possible, the `README.md` **SHOULD**
    explain how to mount a volume to set the configuration.

-   Where configuration occurs via a `config` file, and the image cannot be
    driven by `ENV` variables, a sample `config` file **SHOULD** be supplied and
    injected as part of the Docker build. Dockerfiles **SHOULD NOT** copy
    default configuration directly from GitHub.

-   The GitHub repository `README.md` **MUST** have a Docker reference - this is
    a link on the mandatory Docker Pulls `README.md` badge

-   The **ReadtheDocs** GE Installation Documentation **MUST** include
    references to the Docker Hub image, and how to configure it.

## Publication Requirements

-   The GE owner will be responsible for Docker publication and maintenance
    operations. Docker builds **SHOULD** be automated. GE Owner's build should
    be triggered by git push, FIWARE's one will be triggered by new tagged
    releases.

-   Docker containers **MUST** be tested before being published to the
    community. Error in Docker materials of a GE will be considered as critical
    and **MUST** be fixed immediately.

-   Maintenance and release of interim point releases **MUST** be done using the
    GE Owner own contributor account.

-   A web-hook **MUST** be added so that the FIWARE Infrastructure is informed
    whenever a release version is tagged.

-   Builds of components which do not successfully integrate with
    `r/fiware/orion/latest` will not be added to the FIWARE account. When change
    have been made, a [SemVer](https://semver.org/) release on the source code
    will be required in order to complete the release. This will kick off the
    FIWARE build. Obviously it is essential that such a build passes the
    mandatory integration tests.

## Recommended best practices

-   Dockerfiles **SHOULD** follow best practices as described
    [here](https://docs.docker.com/articles/dockerfile_best-practices/)

-   Dockerfiles **SHOULD** be based on the latest LTS (Long Term Support)
    release of the base image - e.g. `ubuntu:18.04`, `node:carbon` etc.

-   Although default values **SHOULD** be defined, exposed ports **MUST NOT** be
    fixed, and **MUST** be configurable using `ENV` variables.
    
-   The `MAINTAINER` instruction is deprecated. The `LABEL` instruction is a much 
    more flexible version of this and you should use it instead, as it enables 
    setting any metadata you require, and can be viewed easily, for example 
    with `docker inspect`. See section [Label description content](#label-description-content) 
    for more details.

Dockerfiles should be publicly available, and therefore can be read by outside
developers and can reflect on the quality of the product in question. Although
image size is not everything, there are several ways to reduce the bloat of
docker images and good practice should be followed:

-   Where possible, base the image on `debian:9-slim` rather than `Ubuntu`.

-   Node-based images should use `node-carbon-slim` where possible (which is
    also debian-based)

-   Builds should not package development dependencies and should remove
    unnecessary tools such as `wget`, `curl` and so on - if necessary load these
    tools and remove them within the same layer.

-   Use the `RUN git clone` method of obtaining source code instead of
    `ADD/COPY` in case source code can be deleted

-   Consider adding build-args to be able to download latest/stable/specific
    release of the codebase.

-   Additional alpine-based builds may be requested for some components.

### Label description content

Dockerfiles **SHOULD** put the following labels inside the Dockerfile:

- `maintainer` - the name of the caretaker organization.
- `gitrepo` - where the source code can be found.
- `branch` - the branch the image was built from.
- `release_date` - the date the image was built.
- `contacts` - comma separated partial email addresses of responsible contacts (e.g for security updates)
- `organization` - partial email address(es) of responsible contacts (to avoid full public addresses / spam)

Keep in mind that could be possible predefine some values for these labels and modify then during the
building of the docker image. Most values can be predefined or supplied as part of the automated build 
hook script. In the following example, we have predefined some values in the Dockerfile content and 
during the construction of the docker image, we modify some of them. The reason is to allow the building 
outside of Docker Hub or without specifying the corresponding arguments in the command-line. Note that a 
Docker build hook can be used to automate the date and branch functions. Actually anything that can go 
in the build script (e.g. date) or anything that is predefined by Docker Hub (assuming automated builds 
have been set up.)

```dockerfile
ARG NODE_VERSION=8.16.1-slim
FROM node:${NODE_VERSION}
ARG GITHUB_ACCOUNT=fiware
ARG GITHUB_REPOSITORY=iotagent-ul
ARG DOWNLOAD=latest
ARG SOURCE_BRANCH=master
ARG BUILD_DATE=unknown
ARG VERSION="latest"

ENV DOWNLOAD=${DOWNLOAD}

LABEL maintainer="FIWARE Foundation e.V." \
      gitrepo=https://github.com/${GITHUB_ACCOUNT}/${GITHUB_REPOSITORY} \
      branch=${SOURCE_BRANCH} \
      release_date=${BUILD_DATE} \
      contacts=fernando.lopez,jason.fox \
      organization=fiware.org \
      version=${VERSION}

CMD ["/hello"]
```

For automated builds, a docker hub build hook can be set up, pre-configured with `SOURCE_BRANCH`, `DOCKER_TAG`, and 
`IMAGE_NAME` .- an example can be found [here](https://github.com/telefonicaid/iotagent-ul/blob/master/docker/hooks/build).

```bash
docker build  \
  --build-arg BUILD_DATE="$(date)" \
  --build-arg SOURCE_BRANCH=$SOURCE_BRANCH \
  --build-arg VERSION=$DOCKER_TAG \
  -t $IMAGE_NAME .
```

Finally, we can extract the information from the image executing the following command over a previously created
image.

```bash
docker inspect --format '{{json .Config.Labels}}' test | jq .
```

Produce the following result for the previous docker image example.

```json
{
  "branch": "develop",
  "contacts": "fernando.lopez,jason.fox",
  "gitrepo": "https://github.com/fiware/iotagent-ul",
  "maintainer": "FIWARE Foundation e.V.",
  "organization": "fiware.org",
  "release_date": "Tue Sep 24 11:13:44 CEST 2019",
  "version": "1.0"
}
```

> Note: [jq](https://stedolan.github.io/jq/) program is a “filter” that takes an input, and produces an output in pretty 
> json format.

A statement about how to extract Dockerfile label data using `docker inspect` **SHOULD** also be present in the Docker 
`README.md`. The Docker `README.md is used to provide documentation on Docker Hub.

## Examples

-   [GitHub Repository](https://github.com/telefonicaid/fiware-orion/tree/master/docker)

-   [Docker Hub repository](https://hub.docker.com/r/fiware/orion/)

## Support

Should you have any question please send an email to
[fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org)
