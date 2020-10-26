## Repository Recommendations

<span/>

-   The name of the GitHub Repository **MAY** be _'fiware' + '-' + "Code Name of your FIWARE Generic Enabler "_.
    Example: `fiware-orion`.

-   When the FIWARE Generic Enabler code is spread over various repositories, the FIWARE hyperlinks can be included on
    the `README.md` pertaining to the main repository or at the GH user/organization level.

-   Every repository in GitHub **SHOULD** have at least one branch corresponding to the main development line, usually
    named `master`, and a certain number of additional branches/tags corresponding to releases.

-   Every repository in GitHub **SHOULD** comply with the GitHub recommended community standards checklist - e.g.
    `https://github.com/Fiware/developmentGuidelines/community`

-   Every repository in GitHub **SHOULD** have a one line repository description - the description **SHOULD NOT** be
    left blank.

-   Where **Read the Docs** documentation exists for a repository in GitHub, the GitHub repository URL **SHOULD** link
    back to the latest **Read the Docs** documentation - the URL **SHOULD NOT** be left blank.

-   Every repository in GitHub **SHOULD** include a list of related topics including the following:

    -   `fiware`.
    -   The name of the most frequently used related tag on Stack Overflow e.g. `fiware-orion`, `kurento`.

-   Other relevant descriptive tags e.g. `contextual-data`, `iot-agent`, `security`, etc. **MAY** be added.

-   When a GitHub repository is a sample code one related to this FIWARE Generic Enabler, it **SHOULD** also add the
    relevant Stack Overflow tag for it e.g. a python script generating context data for Orion should also include the
    `fiware-orion` tag.

## Continuous Integration

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#test">&#x24D2;</a>
FIWARE Generic Enabler projects developed as open source **SHOULD** have a **public continuous integration system**.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#test_continuous_integration">&#x24D2;</a>
The continuous integration system **SHOULD** be running **every time a new Pull Request** (PR) is done. As a result, the
PR owner can know in advance if this code is breaking something.

Before landing new code, the continuous integration system **MAY** be run in a temporary branch that merge the Pull
Request and the destination branch. Nonetheless, in the event of continuous integration **errors** the (offending) code
**MUST** be **backed out** or a fix **SHOULD** be provided urgently. Use git revert for the former.

[Travis-CI](https://travis-ci.org/) **MAY** be your **continuous integration system** as it is super-easy to integrate
it with GitHub. Jenkins is another popular tool which has the advantage of being able to run on different Operating
Systems.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#test_most">&#x24D2;</a>
Unit tests coverage **MAY** be provided using open source tools like [coveralls](https://coveralls.io/). See an example
in [Wirecloud](https://github.com/Wirecloud/wirecloud)

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#test">&#x24D2;</a> You
**MUST** include **Travis badges** (or other badges) in your `README.md` file. Travis badges can be used to report the
current status of your build, (it **SHOULD** be green!).

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#test_policy">&#x24D2;</a>
As new functionality is added to the software, tests of that functionality **MUST** be added.

## Tracking

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#discussion">&#x24D2;</a>
A Tracking system **MUST** be used in order to **manage the development work**. Such tracking system **MUST** include at
least all the bugs/known issues of your component.

The Tracking system **SHOULD** be **public**. You **MAY** use the [JIRA](https://jira.fiware.org) as a **public tracking
tool**. GitHub Issues **MAY** be other relevant solution to keep this tracking system.

When a commit is actually solving a bug/issue there **MUST** be a **cross-reference** between the commit message and the
corresponding bug/issue in the Tracking System.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#report_responses">&#x24D2;</a>
When users report a new **bug**, it **SHOULD** be given an **estimation** of when the bug will be solved. If the bug is
consider minor or a very edge case and it will not be resolved, it **SHOULD** be marked as 'WontFix' and closed. This
decision **MUST** be **communicated** to the reporter together with a suggested workaround.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#repo_public">&#x24D2;</a>
The **roadmap** of your component **SHOULD** be **public**. Please check the
[General Roadmap Requirements](GE_Requirements.md#roadmap)

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#enhancement_responses">&#x24D2;</a>
Be prepared for **external contributions**. When someone makes a Pull Request be responsive and consider carefully the
proposal made. If you want to **create community** around your component you **SHOULD** be open minded. On the other
hand, code authored by external contributors **SHOULD** not break the basic design principles of your component. Be
prepared for trade-offs.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1?criteria_level=1#dco">&#x24D2;</a>
When someone makes a Pull Request, they **MUST** sign-up to the harmonized
[Individual Contributor License Agreement](https://fiware.github.io/contribution-requirements/individual-cla.pdf)

## Code Quality

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#static-analysis">&#x24D2;</a>
Project repositories **SHOULD** automate coding formatting and run code linters/style checkers as part of the CI testing
process where possible - e.g. **Checkstyle**, **Lint4j**, **ESLint**, etc. A list of suitable tools can be found at:
`https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis`

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#vulnerabilities_critical_fixed">&#x24D2;</a>
To attract active support community, code **SHOULD** regularly be upgraded to the latest LTS libraries and versions of
dependencies - e.g. Java 8,9,10 rather than Java 1.4; ECMAScript 6 rather than ECMAScript 5 etc. Ideally such changes
can also be applied automatically, but **MUST** be tested.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#vulnerabilities_fixed_60_days">&#x24D2;</a>
Versions of dependent libraries with known vulnerabilities **SHOULD** be upgraded as soon as possible.

You **SHOULD** include **Snyk badges** (or other badges) in your `README.md` file. Snyk can be used to report the
vulnerabilities of your build, (it **SHOULD** be green!).

## Documentation

Apart from meeting the [General Documentation Requirements](GE_Requirements.md#documentation-requirements) the following
guidelines apply.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#english">&#x24D2;</a> To
avoid documentation inconsistencies, **development related** documents **MUST** be handled in the same way than Source
Code, this implies:

-   **Developer oriented** documentation in English **MUST** be included as part of the GitHub content.

-   **Markdown** (.md) is the recommended format for document files. Restructured Text (reST) might be used as well.

-   Additional developer oriented documentation (advanced topics) **MUST** be present in a '/doc' folder at the root of
    your repository (or in an specific documentation repository associated to the FIWARE Generic Enabler). It is
    noteworthy that _you **MUST** use an approved markup notation format if you want to benefit from automatic
    documentation generation systems (Read the Docs)_.

    -   [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) is preferred for simple documents.
    -   [ReStructuredText](https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst) is an acceptable
        alternative for complex documentation.

-   Code and documentation **MUST** be synced. To this aim, every **Pull Request** with any impact in existing
    documentation **SHOULD** include any related **documentation changes**.

-   **Inconsistencies** or lacks of documentation **SHOULD** be detected in Code Reviews and QA phases, opening **bugs**
    when necessary.

### Developer Oriented Documentation (**Read the Docs**)

The name of the **project** on **Read the Docs** **SHOULD** match the Stack Overflow tag and Docker image name, e.g.
`fiware-orion` => `https://hub.docker.com/r/fiware/orion` => `https://fiware-orion.rtfd.io`.

Admin access to each **Read the Docs** documentation project **MUST** be granted to multiple accounts. This **SHOULD**
include the current owner of the enabler, and **MAY** also be granted the `fiware` user account - this avoids lock-out
in case an individual administrator is unavailable.

The Documentation **title** on **Read the Docs** (i.e. the `site_name` within the `mkdocs.yml`) **MUST** reflect the
name of the enabler. The title **MAY** match the Stack Overflow tag or alternatively the `site_name` **MAY** consist of
the enabler name without the `fiware` prefix.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#documentation_basics">&#x24D2;</a>
The basic format of the Developer Documentation **SHOULD** consist of the following sections in the following order:

-   Getting Started **SHOULD** - simple responses from the FIWARE Generic Enabler - e.g. `/version` endpoint.

-   User/Programmer's Guide **MUST** - how to use the FIWARE Generic Enabler.

-   Installation/Admin Guide **MUST** - how to install the FIWARE Generic Enabler, both directly from source and via
    Docker.

-   Deprecated Functionality **MAY** - any functionality that is no longer supported or deprecated.

Running tests, contributing code & etc. **SHOULD** be linked directly from the `README.md`, but **SHOULD NOT** be part
of the **Read the Docs** Documentation - the justification is that many users of the software are not interested in
contributing, but need to find user instructions alone without bloat in the text.

Table-of-Contents listings **MAY** be added at the head of each file, but **MUST** come directly after the main `<h1>`
header, and **MUST NOT** be preceded by `<h2>` **Table of Contents** Header of their own. This means the Table of
Contents can be used for navigation if reading the unstyled Markdown files on GitHub, but can be hidden using CSS within
the **Read the Docs** documentation itself and avoid duplication with the sidebar Navigation.

Markdown for **Read the Docs** **MUST NOT** use HTML rendering such as `<a>` tags as the navigation is unpredictable and
may no longer work correctly in **Read the Docs**. An exception can be made for documentation using an extended
character set (e.g. Japanese) which require these tags for headings.

Markdown for **Read the Docs** may use `<h1>...<h6>` HTML headers if necessary to suppress entries in the **Read the
Docs** sidebar.

## Configuration

<span style="color:#233c68;">&#x24D5;</span> FIWARE Generic Enablers **SHOULD** be configurable through a `config` file.

<span style="color:#233c68;">&#x24D5;</span> Docker images for the FIWARE Generic Enablers **SHOULD** be configurable
through `ENV` variables. Where this is not possible or desirable, the `README.md` **MUST** explain how to mount a volume
to set the configuration.

<span style="color:#233c68;">&#x24D5;</span> If the FIWARE Generic Enabler can be configured through a config file, a
**template/example** configuration file **MUST** be present and fully aligned with every version. It **MAY** be
interesting to provide a fully filled in configuration file just to test it.

The config file **MUST** be seen as part of the documentation (for integrators and deployers). So it is mandatory to
**document every config param**, its available options and operation advices.
[Redis configuration](https://github.com/redis-io/redis/blob/unstable/redis.conf) is an illustrative example.

## Software Releases (source code)

Apart from meeting, the general [Release Requirements](GE_Requirements.md#releases) the following guidelines apply.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#version_semver">&#x24D2;</a>
Each code release **SHOULD** be properly **tagged** in your GitHub repository.

Each component **SHOULD** always show a consistent view in the “Releases” and “Tags” tabs at GitHub.com. Examples:

-   `https://github.com/telefonicaid/fiware-orion/releases`

-   `https://github.com/telefonicaid/fiware-orion/tags`

The release notes **SHOULD** include links for downloading the source code.

<a style="color:red!important" href="https://bestpractices.coreinfrastructure.org/en/projects/1#release_notes">&#x24D2;</a>
The **release notes** associated to each Release **SHOULD** include the **change log** for that release, i.e. the list
of changes regarding the previous version, including (if possible) links to the **GitHub issues** related to each
change.

It is not needed to maintain the different branches corresponding to the existing releases once that the corresponding
tag for the release is created. Additionally, every time one branch is merged into another, the branch that is merged in
becomes stale, therefore it is a good approach deleting those branches to prevent clutting up your repository.

## Binary Releases

<span style="color:#233c68;">&#x24D5;</span> FIWARE Generic Enablers **MUST** provide Docker containers according to
[Docker Guidelines](docker.md).

## Additional Repository Content

Files describing the **Licensing and Contribution Policy** **MUST** be included in the repository. Please check the
[General GE Licensing Requirements](GE_Requirements.md#licensing-requirements). They **MUST** be consistent with those
reflected in the [FIWARE Catalogue](https://github.com/FIWARE/catalogue).

## Developer Support

Apart from meeting the general
[Ecosystem Support and Quality Requirements](GE_Requirements.md#ecosystem-support-and-quality-requirements) the
following guidelines apply:

Where relevant, [Stack Overflow](http://stackoverflow.com) **SHOULD** be used for thorough technical questions. Educate
your users to **tag** their questions properly in Stack Overflow.

Each FIWARE Generic Enabler **MUST** be associated to an Stack Overflow tag. Such tag could be specific for a FIWARE
Generic Enabler or default to a chapter generic tag, for instance `fiware-iot`.

Stack Overflow tags **SHOULD** be of the form `fiware-<GE codename>`. Example `fiware-orion`. Creating new tags requires
Stack Overflow Karma. You **MAY** ask someone from the FIWARE community with enough Karma to create tags for your FIWARE
Generic Enabler. Otherwise you can use the [FIWARE Q&A](https://ask.fiware.org) platform.

-   **Exception to the rule:** In the case the FIWARE Generic Enabler is associated to an existing tag (e.g. the tag was
    created before that component joined FIWARE), it could be used instead of the usual `fiware-XXXX` as an exception,
    as long as the two following conditions occur:

    -   The tag clearly reflect the name of the FIWARE Generic Enabler,
    -   The tag is already widely used in Stack Overflow (i.e. more than 30 questions using it).

Anyway, this is a workaround valid only in the case a tag synonym cannot be created due to reputational constraints.

**New releases** of your components **SHOULD** be announced through different channels: FIWARE Blog, dedicated Twitter
or similar channels, your own Blog, etc.

To build and maintain the FIWARE community, it is essential that the team responsible for each product to openly engage
with the wider development community, therefore responding to User Support requests in a timely manner is a **MUST**.

-   If an external developer has found an issue with existing functionality which cannot be fixed in a timely manner, a
    known issue **MUST** be added to the documentation.

-   If an external developer has found a fixable issue with existing functionality an alternative **workaround**
    **MUST** be provided, and the code patched as soon as possible.

-   If an external developer suggests support for a new feature that it is not implemented / not available, an
    alternative **workaround** **SHOULD** be provided where possible.
