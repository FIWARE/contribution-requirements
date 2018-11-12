## Training Course Guidelines

As a generic enabler matures, the documentation surrounding the component should
also be fleshed out. The **ReadTheDocs**
[User Guide](development.md#developer-oriented-documentation-readthedocs) and
[Installation Guide](development.md#developer-oriented-documentation-readthedocs)
should not be over-expanded with too much extra material, instead additional
supplementary documentation should be created and maintained to allow new users
to become familiar with all aspects of the component.

### Tour Guide

-   For examples see
    [fiwaretourguide.readthedocs.io](https://fiwaretourguide.readthedocs.io/en/latest/iot-agents/introduction/)

The tour guide entry for a Generic Enabler is complementary to the quick start
in the User Guide. It contains essential background information and key concepts
along with a few common HTTP calls illustrating how to use the component. To
avoid bloat, it does **not** include set-up material or `docker-compose` files,
the assumption should be that an installed component already exists and has been
started.

The tour guide entry is aimed at **decision makers** who are weighing up which
context data-based framework they are wanting to use

### Tutorials

-   For examples see
    [fiware-tutorials.readthedocs.io](http://fiware-tutorials.readthedocs.io/en/latest)

Tutorials are a step-by-step series of API calls integrating an Generic Enabler
into a stereotypical FIWARE-based scenario. The current set of tutorials are
based on a supermarket environment. These are suitable for developers who learn
by doing, as the goal of each tutorial will be to add a single new feature to
the existing Smart Supermarket app.

A tutorial should consist of:

-   `README`
-   Postman Collection
-   `docker-compose`
-   bash script for initialization

Only a single new enabler should be introduced in each tutorial. Simple
components may only need a single standalone tutorial, but more complex
components should introduce the basic concepts of the component first and then
subsequent tutorials can build on the previous ones. For example **IoT Agents**
tutorials starts with a tutorial on Ultralight sensors before introducing the
IoT Agent for Ultralight itself and then adding in an MQTT broker.

The tutorials are aimed at **developers** who are learning about a new Generic
Enabler and where it fits within the FIWARE Ecosystem.

### Academy

-   For examples see [youtube.com](https://www.youtube.com/watch?v=dHyVTan6bUY),
    [slideshare.net](https://www.slideshare.net/FI-WARE/fiware-iotidasintroul20v2)
    and [edu.fiware.org](https://edu.fiware.org/mod/url/view.php?id=1001)

Academy courses consist of short (5-10 minute) videos and slide presentations
(with or without audio). These courses are suitable for developers who prefer to
learn by watching and are very useful for an overview of GUI-based components.

Typically video presentations should be hosted on `youtube.com` and slide
presentations on `slideshare.net`. The downloadable sources for presentations
with audio are currently found on the Academy server `edu.fiware.org` but this
may change in the future.

In all cases links to each of the academy courses should be listed and
maintained in the `README` of the GitHub repository of the Enabler itself. It is
essential that out-of-date materials are regularly removed from the list.

### Other "Deep Dive" Presentations

Since attention spans are limited, presentations longer than about 10 minutes
are less suitable as introductory learning materials. Longer, deep-dive
presentations such as those presented during FIWARE summits should be listed
separately in the `README`, since the audience will typically be more advanced -
i.e. returning users rather than new users.

In summary, academy courses are aimed at new **developers** who are interested
in learning about a Generic Enabler in isolation, and deep-dive presentations
are aimed at exisiting **developers** who are interested in expanding their
knowledge.

#### Training Course Badge

A count of links will be maintained for each Generic Enabler within the
**Catalogue** repository.

The training badge **MUST** be displayed at the top of the `README` as shown:

-   `https://img.shields.io/badge/dynamic/json.svg?label=Training&url=https://fiware.github.io/catalogue/json/orion.json&query=$.courses&colorB=brightgreen`

(replace `orion` as necessary)
