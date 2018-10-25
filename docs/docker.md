## Guidelines for GE Dockerization (Containerization)

This page summarizes Guidelines for providing Docker Containers for FIWARE GEs.
[Click here](https://docs.docker.com/engine/understanding-docker/) for an
introduction to Docker.

There are three kinds of guidelines included:

-   MUST Guidelines. They are mandatory and your GE project must conform to
    that.

-   SHOULD Guidelines. They are not mandatory but **highly recommended**.

-   MAY Guidelines. They are nice to have.

## Guidelines

-   At least one Dockerfile (hereby named as 'reference `Dockerfile`'), intended
    to GE users, **MUST** be provided. The base image (Ubuntu, CentOS, etc.) for
    such a Dockerfile might depend on each GE.

-   Hacker-oriented Dockerfiles (intended to GE developers) **MAY** be provided
    as well.

-   Each Docker container **MUST** define the following tags (present at
    [Dockerhub](https://hub.docker.com/):

    -   `latest`: It will correspond to the latest build (latest code snapshot)
        of the GE. It might not be stable.
    -   `stable`: It will correspond to the latest stable release of the GE.
    -   `<release n>`: one tag per relevant and active stable release. The name
        of the tag will correspond to the name assigned to the release in
        GitHub.
    -   `FIWARE_<release n>`: one stable release every six months for all FIWARE
        components. This indicates GEs which will work together

-   The reference Dockerfile **MUST** be present under the `docker` folder of
    the GE repository

-   Should your GE depend on other components (Databases, etc.) you **MUST**
    provide a `docker-compose.yml` file that will allow to instantiate the GE
    together with its dependencies.

-   A `README.md` **MUST** be provided under the `docker` folder. Such a
    `README.md` **MUST** give instructions about how to work with the
    corresponding Docker container. Please bear in mind that such a `README.md`
    will also be included as part of the Dockerhub documentation.
-   The `README.md` **MUST** list all available `ENV` variables that can be
    supplied to the Docker Image

-   If the Docker file hides sensitive information (e.g. passwords) using Docker
    Secrets, the `README.md` **MUST** list all available `ENV` variables which
    have an equivalent `_FILE` that can be supplied by secrets.

-   It **MUST** be possible to supply sensitive information using the Docker
    Secrets mechanism as well as plain text variables for testing. Sensitive
    information (e.g. passwords) **MUST NOT** be passed in plain text - `ENV`
    variables alone.

-   It **SHOULD** be possible to configure the GE config entirely through -
    `ENV` variables. Where this is not possible, the `README.md` **MUST**
    explain how to mount a volume to set the configuration.

-   Where configuration occurs via a `config` file, and the image cannot be
    driven by `ENV` variables, a sample `config` file **MUST** be supplied and
    injected as part of the Docker build. Dockerfiles **MUST NOT** copy default
    configuration directly from GitHub.

-   A GE's Docker **MUST** be published at least under the 'fiware' account on
    DockerHub (if possible, please avoid the term 'fiware' in your repository
    name, as the username already contains it).

The GE owner will be responsible for publication and maintenance operations. The
publication method will be through the 'Automatic Build Procedure' which allows
to link a GitHub repository to a Dockerhub one (and keep them in sync). In order
to get access to that account and proceed with the publication, please get in
touch with the FIWARE team at
[fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org).

-   Dockerfiles and Dockerhub repositories **MUST** be linked from the FIWARE
    Catalogue according to the Guidelines defined by the
    [FIWARE Catalogue](http://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/Working_with_the_FIWARE_catalogue#Creating_instances).

-   The GitHub repository `README.md` **MUST** have a Docker reference - this is
    a link on the mandatory Docker Pulls `README.md` badge

-   The **ReadtheDocs** GE Installation Documentation **MUST** include
    references to the Docker Hub image, and how to configure it.

-   Docker containers **MUST** be tested before being published to the
    community. Error in Docker materials of a GE will be considered as critical
    and **MUST** be fixed immediately.

-   Dockerfiles **SHOULD** follow best practices as described
    [here](https://docs.docker.com/articles/dockerfile_best-practices/)

-   Dockerfiles **SHOULD** be based on the latest LTS release of the base
    image - e.g. `ubuntu:18.04`, `node:carbon` etc.

-   Although default values **SHOULD** be defined, exposed ports **MUST NOT** be
    fixed, and **MUST** be configurable using `ENV` variables.

## Examples

-   [GitHub Repository](https://github.com/telefonicaid/fiware-orion/tree/master/docker)

-   [Docker Hub repository](https://registry.hub.docker.com/u/fiware/orion/)

## Support

Should you have any question please send an email to
[fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org)
