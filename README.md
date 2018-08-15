# FIWARE Platform Development Guidelines

![FIWARE Documentation](https://img.shields.io/badge/FIWARE-Documentation-000000.svg?logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABsAAAAVCAYAAAC33pUlAAAABHNCSVQICAgIfAhkiAAAA8NJREFUSEuVlUtIFlEUx+eO+j3Uz8wSLLJ3pBiBUljRu1WLCAKXbXpQEUFERSQF0aKVFAUVrSJalNXGgmphFEhQiZEIPQwKLbEUK7VvZrRvbr8zzjfNl4/swplz7rn/8z/33HtmRhn/MWzbXmloHVeG0a+VSmAXorXS+oehVD9+0zDN9mgk8n0sWtYnHo5tT9daH4BsM+THQC8naK02jCZ83/HlKaVSzBey1sm8BP9nnUpdjOfl/Qyzj5ust6cnO5FItJLoJqB6yJ4QuNcjVOohegpihshS4F6S7DTVVlNtFFxzNBa7kcaEwUGcbVnH8xOJD67WG9n1NILuKtOsQG9FngOc+lciic1iQ8uQGhJ1kVAKKXUs60RoQ5km93IfaREvuoFj7PZsy9rGXE9G/NhBsDOJ63Acp1J82eFU7OIVO1OxWGwpSU5hb0GqfMydMHYSdiMVnncNY5Vy3VbwRUEydvEaRxmAOSSqJMlJISTxS9YWTYLcg3B253xsPkc5lXk3XLlwrPLuDPKDqDIutzYaj3eweMkPeCCahO3+fEIF8SfLtg/5oI3Mh0ylKM4YRBaYzuBgPuRnBYD3mmhA1X5Aka8NKl4nNz7BaKTzSgsLCzWbvyo4eK9r15WwLKRAmmCXXDoA1kaG2F4jWFbgkxUnlcrB/xj5iHxFPiBN4JekY4nZ6ccOiQ87hgwhe+TOdogT1nfpgEDTvYAucIwHxBfNyhpGrR+F8x00WD33VCNTOr/Wd+9C51Ben7S0ZJUq3qZJ2OkZz+cL87ZfWuePlwRcHZjeUMxFwTrJZAJfSvyWZc1VgORTY8rBcubetdiOk+CO+jPOcCRTF+oZ0okUIyuQeSNL/lPrulg8flhmJHmE2gBpE9xrJNkwpN4rQIIyujGoELCQz8ggG38iGzjKkXufJ2Klun1iu65bnJub2yut3xbEK3UvsDEInCmvA6YjMeE1bCn8F9JBe1eAnS2JksmkIlEDfi8R46kkEkMWdqOv+AvS9rcp2bvk8OAESvgox7h4aWNMLd32jSMLvuwDAwORSE7Oe3ZRKrFwvYGrPOBJ2nZ20Op/mqKNzgraOTPt6Bnx5citUINIczX/jUw3xGL2+ia8KAvsvp0ePoL5hXkXO5YvQYSFAiqcJX8E/gyX8QUvv8eh9XUq3h7mE9tLJoNKqnhHXmCO+dtJ4ybSkH1jc9XRaHTMz1tATBe2UEkeAdKu/zWIkUbZxD+veLxEQhhUFmbnvOezsJrk+zmqMo6vIL2OXzPvQ8v7dgtpoQnkF/LP8Ruu9zXdJHg4igAAAABJRU5ErkJgggA=)
[![License: MIT](https://img.shields.io/github/license/fiware/developmentGuidelines.svg)](https://opensource.org/licenses/MIT)

This guide is intended to describe the recommended practices for **FIWARE Platform Development**, particularly for those projects which deal
with the development of a GE or accompanying module.


There are three kinds of guidelines included:

* MUST Guidelines. They are mandatory and your GE project must conform to that.

* SHOULD Guidelines. They are not mandatory but **highly recommended** if you want to have a mature development process.

* MAY Guidelines. They are nice to have.

The Guide assumes that the reader knows the basics of Github, Travis, test driven development and continous integration.
If that is not the case please read one of the many tutorials available on the Internet.

## Summary of MUST Guidelines

* All the [GE General Requirements](GE_Requirements.mediawiki) **MUST** be met.

* The steps described by the [GE Publication Checklist](GE_Checklist.mediawiki) **MUST** be followed.

* A Tracking system MUST be used in order to **manage the development work**. Such tracking system MUST include at least all the bugs/known issues of your component.

* When a commit is actually solving a bug/issue there MUST be a **cross-reference** between the commit message and the corresponding bug/issue in the Tracking System.

* Developer oriented **documentation** MUST be included as part of the **Github content**.

* **Code and documentation** MUST be **synced**. A recommended practice (SHOULD) is that every Pull Request with a direct impact on documentation include documentation changes as well.

* To guarantee that documentation is of high quality, development related **documents** MUST be **peer-reviewed and QA verified**. See [Documentation Guidelines](development.mediawiki#Documentation) for the best documentation practices.

* Should you want to benefit from automatic documentation generation systems, namely, [readthedocs](https://readthedocs.org), you **MUST** use [markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet) for documentation.

* API Specifications MUST be provided. Preferred format is [OpenAPI](https://github.com/OAI/OpenAPI-Specification), a.k.a. Swagger, format.

## Development Guidelines

See [Development Guidelines](development.mediawiki)

## External Contributions

See [External Contributions Guidelines](external_contributions.mediawiki)

## Support

Should you have any questions please contact [mailto:fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org).

---

## License

[MIT](LICENSE) © FIWARE Foundation e.V.
