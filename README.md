# FIWARE Platform Contribution Requirements

[![FIWARE Documentation](https://nexus.lab.fiware.org/repository/raw/public/badges/chapters/documentation.svg)](https://fiware-requirements.rtfd.io)
[![License: CC-BY-4.0](https://img.shields.io/github/license/fiware/developmentGuidelines.svg)](https://creativecommons.org/licenses/by/4.0/)
<br>
[![Documentation](https://img.shields.io/readthedocs/fiware-requirements.svg)](https://fiware-requirements.rtfd.io)

This guide describes the requirements to be fulfilled by any FIWARE Generic
Enabler (GE) as well as the recommended practices for its development.

There are three kinds of requirements included:

-   **MUST** requirements. They are mandatory and your GE project must conform
    to that.

-   **SHOULD** requirements. They are not mandatory but **highly recommended**
    if you want to have a mature development process.

-   **MAY** requirements. They are currently nice to have, but are expected to
    be a sign of further good development process as the tools around them
    mature in the future.

The Guide assumes that the reader knows the basics of
[Github](https://github.com), [Travis](https://travis-ci.org/),
[test driven development](https://en.wikipedia.org/wiki/Test-driven_development)
and
[continuous integration](https://en.wikipedia.org/wiki/Continuous_integration).
If that is not the case please read one of the many tutorials available on the
internet.

## Summary of MUST Requirements

-   All the
    [GE General Requirements](https://fiware-requirements.readthedocs.io/en/latest/GE_Requirements)
    are **MUST** requirements.

-   The steps described by the
    [GE Publication Checklist](https://fiware-requirements.readthedocs.io/en/latest/GE_Checklist)
    **MUST** be followed.

-   A Tracking system MUST be used in order to **manage the development work**.
    Such tracking system MUST include at least all the bugs/known issues of your
    component.

-   When a commit is actually solving a bug/issue there MUST be a
    **cross-reference** between the commit message and the corresponding
    bug/issue in the Tracking System.

-   Developer oriented **documentation** MUST be included as part of the
    **GitHub content**.

-   **Code and documentation** MUST be **synced**. A recommended practice
    (SHOULD) is that every Pull Request with a direct impact on documentation
    include documentation changes as well.

-   To guarantee that documentation is of high quality, development related
    **documents** MUST be **peer-reviewed and QA verified**. See
    [Documentation Guidelines](https://fiware-requirements.readthedocs.io/en/latest/development/index.html#documentation)
    for the best documentation practices.

-   Should you want to benefit from automatic documentation generation systems,
    namely, [ReadtheDocs](https://readthedocs.org), you **MUST** use an approved
    markup notation

    -   [Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)
        is preferred for simple documents.
    -   [restructuredtext](https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst)
        is an acceptable alternative for complex documentation.

-   API Specifications MUST be provided. Preferred format is
    [OpenAPI](https://github.com/OAI/OpenAPI-Specification), a.k.a. Swagger,
    format.

## Development Requirements

See
[Development Guidelines](https://fiware-requirements.readthedocs.io/en/latest/development)

## External Contributions

See
[External Contributions Guidelines](https://fiware-requirements.readthedocs.io/en/latest/external_contributions)

## Support

Should you have any questions please contact
[mailto:fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org).

## Impact on Rating and Continuous Improvement

To further clarify, all mature Generic Enablers **MUST** comply with all
"**MUST**" requirements, failure to do so will result in a written warning and a
requirement to comply within a given period of time. Mature Generic Enablers
which make no effort to fulfill the gaps in their commitments, will be
quarantined and will be removed from the list of Enablers.

It is accepted that Incubated Enablers may not currently comply with all
"**MUST**" requirements, but are expected to be working towards fulfilling them.
All of the "**MUST**" requirements must be fulfilled before the incubation
period is complete.

In addition, all Generic Enablers are expected to continuously improve and
strive to apply industry best practises by fulfilling as many "**SHOULD**" and
"**MAY**" requirements as they can. The quality of each enabler will be checked
against the guideline list, failure to apply guidelines will result in a lower
quality rating - for example, an enabler fulfilling only 20% of the SHOULD list
could be rated as "poor", whereas an enabler fulfilling all of the SHOULD list
could be rated as "good". The fulfillment of a high proportion of "**MAY**"
guidelines (where applicable) would result in an "excellent" rating.

In an effort to maintain a commitment to continuous improvement, it should be
noted that existing requirements will be periodically reviewed, and guidelines
may be re-rated to a higher category. At some point, an existing "**SHOULD**"
guideline may be re-rated as "**MUST**" for example. The owners of each enabler
will be informed whenever a requirement is due to be added or modified, and
there will be a grace period of at least one month before the stricter rating
will be applied on assessments.

---

## License

[CC-BY-4.0](LICENSE) - FIWARE Foundation e.V.
