## Requirements Checklist

This section defines how to apply to become a FIWARE Generic Enabler, the role of Incubated Generic Enablers and how to
transition to full membership as a FIWARE GE.

### New Generic Enabler

This checklist is intended to inform new FIWARE GE owners of the steps that have to be taken in order to publish a new
FIWARE GE.

Any doubt or request to the FIWARE Foundation shall be made by sending an email to
[fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org).

The following minimal requirements must be met before a new contribution can be considered as an Incubated Generic
Enabler. The acceptance can take time, for instance to allow studying the quality of the product, internal architecture,
software design, code cleanliness etc.

<span style="color:#233c68;">&#x24D5;</span> All New Generic Enablers **MUST** be presented to the TSC for candidature
and accepted into an existing Chapter.

<span style="color:#233c68;">&#x24D5;</span> A New Generic Enabler **MUST** show how it integrates within the overall
FIWARE Architecture.

<span style="color:#233c68;">&#x24D5;</span> A New Generic Enabler **MUST** sign-up to the harmonized [Entity Contributor License Agreement](https://fiware.github.io/contribution-requirements/entity-cla.pdf)

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#repo_public">&#x24D2;</a>
The codebase **MUST** be available on [GitHub](https://github.com).

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#floss_license">&#x24D2;</a>
The GitHub repository **MUST** include an appropriate Open Source License - see
[https://choosealicense.com/](https://choosealicense.com/).

<span style="color:#233c68;">&#x24D5;</span> For functional readiness at a minimum, a new incubated enabler **MUST** be
able to be instantiated directly in a running state by any competent developer without the need to refer to other
dependent technologies - for example:

-   [Keyrock](https://fiware-idm.readthedocs.io/en/latest/) relies on MySQL, but a working MySQL can be easily
    instantiated by Docker and minimal data is seeded by Keyrock - the database volume can be persisted. Knowledge of
    SQL is unnecessary for use.
-   An [IoT Agent](https://iotagent-node-lib.readthedocs.io/) can have a dependency on MongoDB - the volumes are exposed
    so that the data will be persisted if the Docker container goes down. Alternatively an IoT Agent can be memory
    based, but all configuration can be set up using a config file or Docker params and then data injected by HTTP
    requests. An understanding of MongoDB is unnecessary to get it to work.
-   [QuantumLeap](https://quantumleap.readthedocs.io/) works with Grafana and Crate-DB - appropriate set-up and docker
    compose are available in the Quick Start. Quantum Leap can be used without in depth knowledge of Crate-DB.

<span style="color:#233c68;">&#x24D5;</span> For all webservice components, a
[Dockerfile](https://docs.docker.com/engine/reference/builder/) **MUST** be available within the code-base.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#documentation_interface">&#x24D2;</a>
Basic documentation **MUST** exist in Markdown and **MUST** be complete enough for usage of the component:

-   <span style="color:#233c68;">&#x24D5;</span> A Quick Start guide.
-   <span style="color:#233c68;">&#x24D5;</span> Admin Installation instructions - how to create instances:
    -   Standalone using configuration files.
    -   Using Docker/Docker-compose and injecting `ENV` variables.
-   <span style="color:#233c68;">&#x24D5;</span> Developer Documentation - how to call the API programmatically.
-   <span style="color:#233c68;">&#x24D5;</span> User Documentation - how to use the GUI.
-   <span style="color:#233c68;">&#x24D5;</span> Apiary file (where necessary).

<span style="color:#233c68;">&#x24D5;</span> For a stateful component, the state **MUST** be persistable between
instantiations, additional manual set-up **MUST** not be required.

<span style="color:#233c68;">&#x24D5;</span> There **MUST** be a commitment that the team behind the product will follow
through with completing the remaining Incubated requirements within a reasonable time frame.

#### Submission Checklist

> **Note:** A formal application must be made using the attached
> [Application Form](https://docs.google.com/forms/d/e/1FAIpQLSdp_QkAG8p5XJK-WDB1xPNY9e4VCvNEJyxwugBvMI6uSPe3fA/viewform?c=0&w=1)

The following information **MUST** be submitted to FF Staff:

<span style="color:#233c68;">&#x24D5;</span> The URL of all of the GitHub Repositories holding the code base.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#version_semver">&#x24D2;</a>
The version number of the initial release to be included in the catalogue - this **MUST** correspond to a real release
tag found on the GitHub repository.

<span style="color:#233c68;">&#x24D5;</span> The location of the official `Dockerfile`, so an “official” FIWARE docker
image can be set up from the FIWARE account.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#documentation_basics">&#x24D2;</a>
The URL for the official documentation - ideally this URL should be a **Read the Docs** project.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#bus_factor">&#x24D2;</a>
The name and the email of a representative who will take the role of the owner/caretaker of the Generic Enabler.

<span style="color:#233c68;">&#x24D5;</span> A sample **elevator pitch** (one sentence) and the **What is?** and **Why
use?** texts (one paragraph each) describing the Generic Enabler in the same manner as the other Generic Enablers.

-   Example - [Elevator Pitches](https://www.fiware.org/developers/catalogue/)
-   Example - [What is text?](https://github.com/Fiware/catalogue/blob/master/core/README.md#what-is-orion)
-   Example - [Why Use text?](https://github.com/Fiware/catalogue/blob/master/core/README.md#why-use-orion)

### Incubated Generic Enabler

The following items are not specific requirements, but are expected requirements to be fulfilled within a few months of
acceptance with the co-operation of the FIWARE Staff and the team behind the contributed component:

-   New entry in the [FIWARE Catalogue](https://www.fiware.org/developers/catalogue/) under the corresponding Chapter
    agreed at TSC Level. See also
    [Working with the FIWARE catalogue](https://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/Working_with_the_FIWARE_catalogue).
-   Mirroring GitHub Webhook properly configured. See [webhooks](repo_webhook.md) (Ask FIWARE Foundation to configure the mirroring).
-   **Read the Docs** project available and styled using the FIWARE CSS and Chapter CSS. See
    [fiware-orion.readthedocs.org](https://fiware-orion.readthedocs.io) as an example.
-   Automatic documentation generation **MUST** be configured. See
    [mkdocs.yml](https://github.com/telefonicaid/fiware-orion/blob/master/mkdocs.yml) as a reference on how to configure
    **Read the Docs**.
-   Analytics **MUST** be configured for the **Read the Docs** portal as described by
    [analytics](analytics_readthedocs.md).
-   Docker image **MUST** be available in [FIWARE's Dockerhub account](https://hub.docker.com/Dockerhub).
-   Roadmap **MUST** be available at one of the following:
    -   Promoted on GitHub and linked in the
        [Current Roadmap](https://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/Current_Supported_Features_and_Roadmap_in_FIWARE).
    -   Promoted in a publicly available document on the web and linked at
        [Current Roadmap](https://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/Current_Supported_Features_and_Roadmap_in_FIWARE).
    -   Full text found within the
        [Current Roadmap](https://forge.fiware.org/plugins/mediawiki/wiki/fiware/index.php/Current_Supported_Features_and_Roadmap_in_FIWARE).
-   Release schedule **MUST** be aligned with [release requirements](GE_Requirements.md#releases).
-   Access **MUST** be provided to the corresponding information in order to see your component reflected in the
    [monitoring tool](https://docs.google.com/spreadsheets/d/1yyZNUlAPDcqjnD-gIoGOd5SZfVDJXO36G75xTDL0HgA/edit#gid=0)
    (Ask FIWARE Foundation Staff).

It is accepted that Incubated Enablers may not currently comply with all "**MUST**" requirements of the
[Development Guidelines](development.md), but are expected to be working towards fulfilling them. Commitment to
completing the transition to a full member is tracked as part of the FIWARE Quality Assurance testing, and insufficient
progress on issues will eventually result in the enabler being quarantined or be removed from the list of Enablers.

### Mature Generic Enabler (Full Member)

<span style="color:#233c68;">&#x24D5;</span> All of the FIWARE "**MUST**" requirements (marked
<span style="color:#233c68;">&#x24D5;</span> ) **MUST** be fulfilled before the incubation period is complete.

<span style="color:red">&#x24D2;</span> The CII Best Practices Badge **MUST** be displayed
[![.](https://bestpractices.coreinfrastructure.org/projects/24/badge)](#) and passing.

<span style="color:#233c68;">&#x24D5;</span> The enabler should have demonstrated that it fulfills a real need within
the FIWARE ecosystem, and statistics showing a credible level of adoption and community support **MUST** be presented to
the TSC.

#### Ongoing Commitment

Having achieved full membership, this is the expected standard for membership going onward. All the requirements for
marked <span style="color:#233c68;">&#x24D5;</span> or <span style="color:red">&#x24D2;</span> **MUST** be met.

> To further clarify, failure to do so will result in a written warning and a requirement to comply within a given
> period of time. Mature Generic Enablers which make no effort to fulfill the gaps in their commitments, will be
> quarantined and will be removed from the list of Enablers.

-   A Stack Overflow tag for the component is registered (Ask FIWARE Foundation Staff)
-   Where it is suitable to provide a global instance of a service, a public instance may be deployed in the FIWARE
    Foundation infrastructure and maintained by the team in collaboration with the FIWARE Foundation team
    (Ask FIWARE Foundation Staff).
-   A tour guide entry is provided - see
    [fiwaretourguide.readthedocs.io](https://fiwaretourguide.readthedocs.io/en/latest/iot-agents/introduction/).
-   A tutorial is provided (See some examples at
    [fiware-tutorials.readthedocs.io](http://fiware-tutorials.readthedocs.io/en/latest)).
