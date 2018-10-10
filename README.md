# FIWARE Platform Development Requirements

![FIWARE Documentation](https://img.shields.io/badge/FIWARE-Documentation-000000.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABsAAAAVCAYAAAC33pUlAAAABHNCSVQICAgIfAhkiAAAA8NJREFUSEuVlUtIFlEUx+eO+j3Uz8wSLLJ3pBiBUljRu1WLCAKXbXpQEUFERSQF0aKVFAUVrSJalNXGgmphFEhQiZEIPQwKLbEUK7VvZrRvbr8zzjfNl4/swplz7rn/8z/33HtmRhn/MWzbXmloHVeG0a+VSmAXorXS+oehVD9+0zDN9mgk8n0sWtYnHo5tT9daH4BsM+THQC8naK02jCZ83/HlKaVSzBey1sm8BP9nnUpdjOfl/Qyzj5ust6cnO5FItJLoJqB6yJ4QuNcjVOohegpihshS4F6S7DTVVlNtFFxzNBa7kcaEwUGcbVnH8xOJD67WG9n1NILuKtOsQG9FngOc+lciic1iQ8uQGhJ1kVAKKXUs60RoQ5km93IfaREvuoFj7PZsy9rGXE9G/NhBsDOJ63Acp1J82eFU7OIVO1OxWGwpSU5hb0GqfMydMHYSdiMVnncNY5Vy3VbwRUEydvEaRxmAOSSqJMlJISTxS9YWTYLcg3B253xsPkc5lXk3XLlwrPLuDPKDqDIutzYaj3eweMkPeCCahO3+fEIF8SfLtg/5oI3Mh0ylKM4YRBaYzuBgPuRnBYD3mmhA1X5Aka8NKl4nNz7BaKTzSgsLCzWbvyo4eK9r15WwLKRAmmCXXDoA1kaG2F4jWFbgkxUnlcrB/xj5iHxFPiBN4JekY4nZ6ccOiQ87hgwhe+TOdogT1nfpgEDTvYAucIwHxBfNyhpGrR+F8x00WD33VCNTOr/Wd+9C51Ben7S0ZJUq3qZJ2OkZz+cL87ZfWuePlwRcHZjeUMxFwTrJZAJfSvyWZc1VgORTY8rBcubetdiOk+CO+jPOcCRTF+oZ0okUIyuQeSNL/lPrulg8flhmJHmE2gBpE9xrJNkwpN4rQIIyujGoELCQz8ggG38iGzjKkXufJ2Klun1iu65bnJub2yut3xbEK3UvsDEInCmvA6YjMeE1bCn8F9JBe1eAnS2JksmkIlEDfi8R46kkEkMWdqOv+AvS9rcp2bvk8OAESvgox7h4aWNMLd32jSMLvuwDAwORSE7Oe3ZRKrFwvYGrPOBJ2nZ20Op/mqKNzgraOTPt6Bnx5citUINIczX/jUw3xGL2+ia8KAvsvp0ePoL5hXkXO5YvQYSFAiqcJX8E/gyX8QUvv8eh9XUq3h7mE9tLJoNKqnhHXmCO+dtJ4ybSkH1jc9XRaHTMz1tATBe2UEkeAdKu/zWIkUbZxD+veLxEQhhUFmbnvOezsJrk+zmqMo6vIL2OXzPvQ8v7dgtpoQnkF/LP8Ruu9zXdJHg4igAAAABJRU5ErkJgggA=)
[![License: CC-BY-4.0](https://img.shields.io/github/license/fiware/developmentGuidelines.svg)](https://creativecommons.org/licenses/by/4.0/)

This guide is describes the requirements to be fulfilled by any FIWARE Generic Enabler (GE) as well as the recommended practices for the development of FIWARE GEs.


There are three kinds of guidelines included:

* **MUST** requirements. They are mandatory and your GE project must conform to that.

* **SHOULD** requirements. They are not mandatory but **highly recommended** if you want to have a mature development process.

* **MAY** requirements. They are currently nice to have, but are expected to be a sign of further good development process as the tools around them mature in the future.

The Guide assumes that the reader knows the basics of Github, Travis, test driven development and continous integration.
If that is not the case please read one of the many tutorials available on the Internet.

### Impact on Rating and Continuous Improvement

To further clarify, all mature Generic Enablers **MUST** comply with all "**MUST**" requirements, failure to do so will
result in a written warning and a requirement to comply within a given period of time. Mature Generic Enablers which
make no effort to fulfill the gaps in their commitments, will be quarantined and will be removed from the list of Enablers.

It is accepted that Incubated Enablers may not currently comply with all "**MUST**" requirements, but are expected to be working towards fulfilling them.
All of the "**MUST**" requirements must be fulfilled before the incubation period is
complete.

In addition, all Generic Enablers are expected to continuously improve and strive to apply industry best practises by
fulfilling as many "**SHOULD**" and "**MAY**" requirements as they can. The quality of each enabler will be checked
against the guideline list, failure to apply guidelines will result in a lower quality rating - for example, an
enabler fulfilling only 20% of the SHOULD list could be rated as "poor", whereas an enabler fulfilling all of the
SHOULD list could be rated as "good". The fulfillment of a high proportion of "**MAY**" guidelines (where applicable)
would result in an "excellent" rating.

In an effort to maintain a commitment to continuous improvement, it should be noted that existing requirements will be
periodically reviewed, and guidelines may be re-rated to a higher category. At some point, an existing  "**SHOULD**"
guideline may be re-rated as "**MUST**" for example. The owners of each enabler will be informed whenever a requirement
is due to be added or modified, and there will be a grace period of at least one month before the stricter rating will
be applied on assessments.



## Summary of MUST Requirements

* All the [GE General Requirements](GE_Requirements.mediawiki) are **MUST** requirements.

* The steps described by the [GE Publication Checklist](GE_Checklist.mediawiki) **MUST** be followed.

* A Tracking system MUST be used in order to **manage the development work**. Such tracking system MUST include at least all the bugs/known issues of your component.

* When a commit is actually solving a bug/issue there MUST be a **cross-reference** between the commit message and the corresponding bug/issue in the Tracking System.

* Developer oriented **documentation** MUST be included as part of the **Github content**.

* **Code and documentation** MUST be **synced**. A recommended practice (SHOULD) is that every Pull Request with a direct impact on documentation include documentation changes as well.

* To guarantee that documentation is of high quality, development related **documents** MUST be **peer-reviewed and QA verified**. See [Documentation Guidelines](development.mediawiki#Documentation) for the best documentation practices.

* Should you want to benefit from automatic documentation generation systems, namely, [ReadtheDocs](https://readthedocs.org), you **MUST** use an approved markup notation
    * [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) is preferred for simple documents.
    * [restructuredtext](https://github.com/ralsina/rst-cheatsheet/blob/master/rst-cheatsheet.rst) is an acceptable alternative for complex documentation.

* API Specifications MUST be provided. Preferred format is [OpenAPI](https://github.com/OAI/OpenAPI-Specification), a.k.a. Swagger, format.

## Development Requirements

See [Development Guidelines](development.mediawiki)

## External Contributions

See [External Contributions Guidelines](external_contributions.mediawiki)

## Support

Should you have any questions please contact [mailto:fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org).

---

## License

[CC-BY-4.0](LICENSE) - FIWARE Foundation e.V.
