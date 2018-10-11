## Checklist for publishing FIWARE Generic Enablers
This checklist is intended to inform new FIWARE GE owners of the steps that have to be taken in order to publish a new FIWARE GE.

Any doubt or request to the FIWARE Foundation shall be made by sending an email to [fiware-help@lists.fiware.org](mailto:fiware-help@lists.fiware.org)

* New entry in the [FIWARE Catalogue](https://catalogue-server.fiware.org) under the corresponding Chapter agreed at TSC Level. See also [Working with the FIWARE catalogue](https://wiki.fiware.org/Working_with_the_FIWARE_catalogue)
* Mirroring Github Webhook properly configured. See [webhooks](repo_webhook.md) (Ask FF to configure the mirroring).
* **ReadtheDocs** portal available and styled using the FIWARE CSS. See [fiware-orion.readthedocs.org](https://fiware-orion.readthedocs.org https://fiware-orion.readthedocs.org) as an example. 
* See [mkdocs.yml](https://github.com/telefonicaid/fiware-orion/blob/master/mkdocs.yml) as a reference on how to configure **ReadtheDocs** for automatic documentation generation. 
* Analytics should be configured for the **ReadtheDocs** portal as described by [analytics](analytics_readthedocs.mediawiki)
* Docker image is available in [FIWARE's Dockerhub account](https://hub.docker.com/Dockerhub)
* FIWARE Development (Must) Guidelines are met. See [Development Guidelines](development.md)
* A Stackoverflow tag for the component is registered (Ask FF Staff)
* Where it is suitable to provide a global instance of a service, a public instance is deployed in the FIWARE Lab and maintained by the FF team (Ask FF Staff)
* Roadmap is available at one of the following:
    * Promoted on Github and linked in the [Current Roadmap](https://wiki.fiware.org/Current_Supported_Features_and_Roadmap_in_FIWARE)
    * Promoted in a publicly available document on the web and linked at [Current Roadmap](https://wiki.fiware.org/Current_Supported_Features_and_Roadmap_in_FIWARE)
    * Full text found within the [Current Roadmap](https://wiki.fiware.org/Current_Supported_Features_and_Roadmap_in_FIWARE)
* Release schedule is aligned with [release requirements](GE_Requirements.md#Releases)
* A tutorial is provided (See some examples at [fiware-tutorials.readthedocs.io](http://fiware-tutorials.readthedocs.io/en/latest))
* Provide access to the corresponding information in order to see your component reflected in the [ monitoring tool](https://docs.google.com/spreadsheets/d/1yyZNUlAPDcqjnD-gIoGOd5SZfVDJXO36G75xTDL0HgA/edit#gid=0 FIWARE - TSC Enablers Dashboard) (Ask FF Staff)

