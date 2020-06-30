## Development Lifecycle Recommendations in FIWARE

## SCM Tool

-   The SCM Tool **MUST** be [GitHub](https://github.com). Accompanying tools or
    plugins that integrate well with GitHub (ex. Gerrit) **MAY** be used.
-   GitHub **MUST** be used during the **whole development lifecycle**.
-   The name of the GitHub Repository **MAY** be _'fiware' + '-' + "Code Name of
    your GE"_. Example: `fiware-orion`.
-   The GitHub Repository content **MUST** meet the
    [GE Publication Requirements](GE_Requirements.md#publication-requirements)
-   When the GE code is spread over various repositories, the FIWARE hyperlinks
    can be included on the `README.md` pertaining to the main repository or at
    the GH user/organization level.

-   Every repository in GitHub **SHOULD** have at least one branch corresponding
    to the main development line, usually named `master`, and a certain number
    of additional branches/tags corresponding to releases.
-   Every repository in GitHub **SHOULD** comply with the GitHub recommended
    community standards checklist - e.g.
    `https://github.com/Fiware/developmentGuidelines/community`
-   Every repository in GitHub **SHOULD** have a one line repository
    description - the description **SHOULD NOT** be left blank
-   Where **ReadtheDocs** documentation exists for a repository in Github, the
    GitHub repository URL **SHOULD** link back to the latest **ReadtheDocs**
    documentation - the URL **SHOULD NOT** be left blank
-   Every repository in GitHub **SHOULD** include a list of related topics
    including the following:
    -   `fiware`
    -   The name of the most frequently used related tag on Stack Overflow e.g.
        `fiware-orion`, `kurento`
-   Other relevant descriptive tags e.g. `contextual-data`, `iot-agent`,
    `security` etc. **MAY** be added.
-   When a GitHub repository is sample code related a Generic Enabler, it
    **SHOULD** also add the relevant Stack Overflow tag for that GE e.g. a
    python script generating context data for Orion should also include the
    `fiware-orion` tag.

## Development Lifecycle

Apart from the minimal, mandatory lifecycle described by the
[GE Requirements](GE_Requirements.md#development-lifecycle) the following
guidelines also apply.

The development lifecycle of a GE **SHOULD** be as follows:

1. When developing a new feature / bug try to **divide the work** into smaller
   parts. For instance, dividing by frontend and backend implementation. There
   can be other criteria that might depend on each feature / bug. The aim of
   this division is to simplify the review process. Big commits are usually hard
   to review, hard to change later and prone to conflicts.

2. Once you have divided the work in parts, the implementation of each part
   **SHOULD** be done in a **different branch** that you will use later to _Pull
   Request_ to the GE Repository. One recommended practice is that you _fork_
   the original repository to your GH account and develop the feature in your
   own branch (which will belong to your own repository). Later, you will make a
   Pull Request from that branch to the GE repository. See
   [branching model](http://nvie.com/posts/a-successful-git-branching-model).

3. The Pull Request **SHOULD** include not only the feature's source code but
   **unit or integration tests** together with relevant documentation.

4. At the time of landing (merging), a Pull Request **SHOULD** include **only
   one commit**. While developing you **MAY** have more than one commit but
   ultimately _only one commit **SHOULD** remain_. For doing so, use the
   [git squash](https://blog.github.com/2016-04-01-squash-your-commits/)
   functionality.

Nonetheless, there can be situations for which a Pull Request might be better
explained with more than one commit. In that particular case you **SHOULD** also
try to squash your commits into functionally coherent blocks. Nonetheless, every
commit message **MUST** be descriptive of what feature or bug the code is
implementing, for instance:

```
ISSUE 345. POST Operation /entities. Part I Parsing Requests.
ISSUE 345. POST Operation /entities. Part II DB Persistence.
ISSUE 345. POST Operation /entities. Part III Rendering Responses.
```

5. Once a Pull Request is done, a **code review** will be performed. Find a
   competent reviewer that can perform a code review. There can be more than one
   reviewer but one of them **SHOULD** be a main developer or technical
   owner/architect of the project. Typically the reviewer will test the feature,
   review the code (style, robustness, structure, performance) and suggest some
   changes. The code review **MUST** be made using the code review facilities
   provided by GitHub.

6. Try to address all the comments suggested by reviewers. If a comment is not
   going to be addressed a rationale **SHOULD** be provided.

7. Wait for a final **positive review**. This **MAY** imply _one or more
   iterations_ over steps 5 and 6.

8. Land (merge) the new code. But before landing **ensure that all tests are
   passing**. Under certain conditions your Pull Request could not be directly
   landed (merged). In that case you would need to rebase your branch with the
   master branch, resolve all conflicts, push them and finally merge the new
   code in the master branch. Nobody can auto-merge their contributions.

9. If later you discover that new code is breaking something _do not hesitate to
   back out the culprit code_. That's the advantage of landing only one commit.
   Backing out code is as easy as `git revert <commit_hash>` .

## Continuous Integration

GE projects developed as open source **SHOULD** have a **public continuous
integration system**.

The continuous integration system **SHOULD** be running **every time a new Pull
Request** (PR) is done. As a result the PR owner can know in advance if her code
is breaking something.

Before landing new code the continuous integration system **MAY** be run in a
temporary branch that merge the Pull Request and the destination branch.
Nonetheless, in the event of continuous integration **errors** the (offending)
code **MUST** be **backed out** or a fix **SHOULD** be provided urgently. Use
git revert for the former.

[Travis-CI](https://travis-ci.org/) **MAY** be your **continuous integration
system** as it is super-easy to integrate it with GitHub. Jenkins is another
popular tool which has the advantage of being able to run on different OS.

Unit tests coverage **MAY** be provided using open source tools like
[ coveralls](https://coveralls.io/). See an example in
[Wirecloud](https://github.com/Wirecloud/wirecloud)

You **MUST** include **Travis badges** (or other badges) in your `README.md`
file. Travis badges can be used to report the current status of your build, (it
**SHOULD** be green!).

## Tracking

A Tracking system **MUST** be used in order to **manage the development work**.
Such tracking system **MUST** include at least all the bugs/known issues of your
component.

The Tracking system **SHOULD** be **public**. You **MAY** use the
[JIRA](https://jira.fiware.org FIWARE) as a **public tracking tool**.

When a commit is actually solving a bug/issue there **MUST** be a
**cross-reference** between the commit message and the corresponding bug/issue
in the Tracking System.

When users report a new **bug**, it **SHOULD** be given an **estimation** of
when the bug will be solved. If the bug is consider minor or a very edge case
and it will not be resolved, it **SHOULD** be marked as 'WontFix' and closed.
This decision **MUST** be **communicated** to the reporter together with a
suggested workaround.

The **roadmap** of your component **SHOULD** be **public**. Please check the
[General Roadmap Requirements](GE_Requirements.md#roadmap)

Be prepared for **external contributions**. When someone makes a Pull Request be
responsive and consider carefully the proposal made. If you want to **create
community** around your component you **SHOULD** be open minded. On the other
hand code authored by external contributors **SHOULD** not break the basic
design principles of your component. Be prepared for trade-offs.

## Code Quality

Project repositories **SHOULD** automate coding formatting and run code
linters/style checkers as part of the CI testing process where possible - e.g.
**Checkstyle**, **Lint4j**, **ESLint** etc. A list of suitable tools can be
found at: `https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis`

To attract active support community, code **SHOULD** regularly be upgraded to
the latest LTS libraries and versions of dependencies - e.g. Java 8,9,10 rather
than Java 1.4; ECMAScript 6 rather than ECMAScript 5 etc. Ideally such changes
can also be applied automatically, but **MUST** be tested.

Versions of dependent libraries with known vulnerabilities **SHOULD** be
upgraded

You **SHOULD** include **Synk badges** (or other badges) in your `README.md`
file. Synk can be used to report the vulnerabilities of your build, (it
**SHOULD** be green!).

## Documentation

Apart from meeting the
[General Documentation Requirements](GE_Requirements.md#documentation-requirements)
the following guidelines apply.

To avoid documentation inconsistencies, **development related** documents
**MUST** be handled in the same way than Source Code, this implies:

-   **Developer oriented** documentation **MUST** be included as part of the
    GitHub content.
-   **Markdown** (.md) is the recommended format for document files.
    Restructured Text (reST) might be used as well.
-   Additional developer oriented documentation (advanced topics) **MUST** be
    present in a '/doc' folder at the root of your repository (or in an specific
    documentation repository associated to the GE). It is noteworthy that _you
    **MUST** use an approved markup notation format if you want to benefit from
    automatic documentation generation systems (ReadTheDocs)_.
    -   [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
        is preferred for simple documents.
    -   [ReStructuredText](https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst)
        is an acceptable alternative for complex documentation.
-   Code and documentation **MUST** be synced. To this aim, every **Pull
    Request** with any impact in existing documentation **SHOULD** include any
    related **documentation changes**.
-   **Inconsistencies** or lacks of documentation **SHOULD** be detected in Code
    Reviews and QA phases, opening **bugs** when necessary.

### Documentation `README.md`

-   A `README.md` **MUST** be always present in the root folder of any
    repository associated to the GE. The purpose of such a document associated
    to a GE is to document:
    -   GE overall description.
    -   How to Deploy the GE (basic/default installation procedure)
    -   How to run tests
    -   A walkthrough guide on using the main APIs
    -   How to get access to the advanced API and Documentation topics

In general the structure of the `README.md` **SHOULD** follow a standard format
such as [standard-readme](https://github.com/RichardLitt/standard-readme).

More specifically, the referred `README.md` **SHOULD** include:

-   Simple GE/Service **Description** and purpose -

    -   The first paragraph **SHOULD** be an **elevator pitch** about the
        purpose of the repository (Since this is displayed on GitHub on mobile)
    -   Include direct **ReadtheDocs** links to the **User Guide**, **Admin
        Guide** in a subsequent introductory paragraph (To allow users to
        navigate directly between code and documentation )
    -   Include information about testbed environments if available

-   Then add a **Table of Contents** to make navigation through the rest of the
    document easier

-   How to **Build & Install**

    -   Make your simplest full stack deployment as easy as possible
    -   Include System requirement info: SO, CPU/Storage Capacity...
    -   Include installation support for your dependencies
    -   Provide a “Hello World” example using curl (basic acceptance test)
    -   Include troubleshooting information for the whole process

-   **API Overview** of the main data flow

    -   It is a tutorial, not a reference. It does not need to be exhaustive, it
        needs to guide the user
    -   Provide always curl examples for this section

-   More **API Examples**

    -   Just the important bits of your API used in examples

-   A link to the **API Reference Documentation**.
    [Open API](https://github.com/OAI/OpenAPI-Specification) **SHOULD** be used.

-   How to **run tests**

    -   End-to-end tests (**SHOULD**). This will be part of the sanity checks
        included in the "Installation & Administration Guide", thus a link will
        be needed.
    -   Unit tests (**SHOULD**)
    -   Performance tests (**MAY**)

-   List of links to **Advanced topics** (/doc folder)
    -   User & Programmers Manual (**MUST**)
    -   Installation & Administration Guide (**MUST**)
    -   Other documents, for instance: HA deployment, detailed architecture,
        Advanced configuration topics, advanced functionalities, ...

### Developer Oriented Documentation (**ReadtheDocs**)

The name of the **project** on **ReadtheDocs** **SHOULD** match the Stack
Overflow tag and Docker image name, e.g. `fiware-orion` =>
`https://hub.docker.com/r/fiware/orion` => `https://fiware-orion.rtfd.io`.

Admin access to each **ReadtheDocs** documentation project **MUST** be granted
to multiple accounts. This **SHOULD** include the current owner of the enabler,
and **MAY** also be granted the `fiware` user account - this avoids lock-out in
case an individual administrator is unavailable.

The Documentation **title** on **ReadtheDocs** (i.e. the `site_name` within the
`mkdocs.yml`) **MUST** reflect the name of the enabler. The title **MAY** match
the Stack Overflow tag or alternatively the `site_name` **MAY** consist of the
enabler name wihout the 'fiware' prefix.

The basic format of the Developer Documentation **SHOULD** consist of the
following sections in the following order

-   Getting Started **SHOULD** - simple responses from the GE - e.g. `/version`
    endpoint
-   User/Programmer's Guide **MUST** - how to use the GE
-   Installation/Admin Guide **MUST** - how to install the GE, both directly
    from source and via Docker
-   Deprecated Functionality **MAY** - any functionality that is no longer
    supported or deprecated

Running tests, contributing code & etc. **SHOULD** be linked directly from the
`README.md`, but **SHOULD NOT** be part of the **ReadtheDocs** Documentation -
the justification is that many users of the software are not interested in
contributing, but need to find user instructions alone without bloat in the
text.

Table-of-Contents listings **MAY** be added at the head of each file, but
**MUST** come directly after the main `<h1>` header, and **MUST NOT** be
preceded by `<h2>` **Table of Contents** Header of their own. This means the
Table of Contents can be used for navigation if reading the unstyled Markdown
files on GitHub, but can be hidden using CSS within the **ReadtheDocs**
documentation itself and avoid duplication with the sidebar Navigation.

Markdown for **ReadtheDocs** **MUST NOT** use HTML rendering such as `<a>` tags
as the navigation is unpredictable and may no longer work correctly in
**ReadtheDocs**. An exception can be made for documentation using an extended
character set (e.g. Japanese) which require these tags for headings.

Markdown for **ReadtheDocs** may use `<h1>...<h6>` HTML headers if necessary to
suppress entries in the **ReadtheDocs** sidebar.

## Configuration

GEs **SHOULD** be configurable through a `config` file.

Docker images for GEs **SHOULD** be configurable. through `ENV` variables. Where
this is not possible or desirable, the `README.md` **MUST** explain how to mount
a volume to set the configuration.

If the GE can be configured through a config file, a **template/example**
configuration file **MUST** be present and fully aligned with every version.

The config file **MUST** be seen as part of the documentation (for integrators
and deployers). So it is mandatory to **document every config param**, its
available options and operation advices.
[Redis configuration](https://github.com/antirez/redis/blob/unstable/redis.conf)
is an illustrative example.

## Software Releases (source code)

Apart from meeting the general
[Release Requirements](GE_Requirements.md#releases) the following guidelines
apply.

Each code release **SHOULD** be properly **tagged** in your GitHub repository.

Each component **SHOULD** always show a consistent view in the “Releases” and
“Tags” tabs at GitHub.com. Examples:

-   `https://github.com/telefonicaid/fiware-orion/releases`

-   `https://github.com/telefonicaid/fiware-orion/tags`

The release notes **SHOULD** include links for downloading the source code.

The **release notes** associated to each Release **SHOULD** include the **change
log** for that release, i.e. the list of changes regarding the previous version,
including (if possible) links to the **GitHub issues** related to each change.

## Binary Releases

GEs **MUST** provide Docker containers according to
[Docker Guidelines](docker.md).

## Additional Repository Content

Files describing the **Licensing and Contribution Policy** **MUST** be included
in the repository. Please check the
[General GE Licensing Requirements](GE_Requirements.md#licensing-requirements).
They **MUST** be consistent with those reflected in the
[FIWARE Catalogue](https://github.com/FIWARE/catalogue).

## Developer Support

Apart from meeting the general
[Ecosystem Support and Quality Requirements](GE_Requirements.md#ecosystem-support-and-quality-requirements)
the following guidelines apply:

Where relevant, [Stack Overflow](http://stackoverflow.com) **SHOULD** be used
for thorough technical questions. Educate your users to **tag** their questions
properly in Stack Overflow.

Each FIWARE GE **MUST** be associated to an Stack Overflow tag. Such tag could
be specific for a GE or default to a chapter generic tag, for instance
`fiware-iot`.

Stack Overflow tags **SHOULD** be of the form `fiware-<GE codename>`. Example
`fiware-orion`. Creating new tags requires Stack Overflow Karma. You **MAY** ask
someone from the FIWARE community with enough Karma to create tags for your GE.
Otherwise you can use the [FIWARE Q&A](https://ask.fiware.org) platform.

-   **Exception to the rule:** In the case the GE is associated to an existing
    tag (e.g. the tag was created before that GE joined FIWARE), it could be
    used instead of the usual `fiware-XXXX` as an exception, as long as the two
    following conditions occur:

        1. the tag clearly reflect the name of the GE,
        2. the tag is already widely used in Stack Overflow (i.e. more than 30 questions using it).

Anyway, this is a workaround valid only in the case a tag synonym cannot be
created due to reputational constraints.

**New releases** of your components **SHOULD** be announced through different
channels: FIWARE Blog, dedicated Twitter or similar channels, your own Blog ...

To build and maintain the FIWARE community, it is essential that the team
responsible for each product to openly engage with the wider development
community, therefore responding to User Support requests in a timely manner is a
**MUST**.

-   If an external developer has found an issue with existing functionality
    which cannot be fixed in a timely manner, a known issue **MUST** be added to
    the documentation.
-   If an external developer has found a fixable issue with existing
    functionality an alternative **workaround** **MUST** be provided, and the
    code patched as soon as possible.
-   If an external developer suggests support for a new feature is not
    implemented / not available, an alternative **workaround** **SHOULD** be
    provided where possible.
