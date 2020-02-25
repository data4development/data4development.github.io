---
title: Welcome
order: 1
---

<img src="/assets/img/logoData4development.png" width="300">

The Data4Development GitHub pages provide technical information about our products.

* Below is a general overview of the components in the system.
* See the [Use cases](/use-cases) for specific types of use.

## IATI Data Validation

The DataWorkbench components collect public IATI data files, process them to produce validation and data quality feedback reports, and make those available via an API and a web front-end. In a schematic overview:

![](overview.drawio.svg)

Each of the components has its own Github repository, with documentation available via this site.

#### [IATI Data Refresher](IATI-data-refresher)

Updates the information about available publishers and datasets from the [IATI Registry](https://iatiregistry.org/), and uses a snapshot repository to update IATI files in the system.

**TBD**: The data refresher will be using the IATI Datastore as the source of IATI files.

#### [IATI Data Validator](/IATI-data-validator)

Generates data quality feedback for IATI files, using both schema validation and business rules validation. The Validator itself is the worker engine that checks the system for unprocessed files.

* The [IATI Rulesets](IATI-Rulesets) repository contains the business rules, and can be integrated in an XML pipeline on its own.
* The formats of the available validation reports are described as part of the documentation of the Validator. The reports are available as files, access to the files and metadata is described in the API documentation.

#### [API](/dataworkbench-api)

Provides the point of entry to services on the cluster. The API can be run in *public* and in *private* mode.

* The *public* mode is exposed via the cluster load balancer, and contains a subset of the available end points.
* The *private* mode is used internally, and offers all end points.

#### [Front end](/dataworkbench-frontend)

Provides the web interface for data quality feedback. The API calls used by the front-end are described as part of the API documentation.

#### [Cluster](/dataworkbench-cluster)

Provides the documentation and configuration of the infrastructure of the DataWorkbench.

## Supporting tools

- [DataWorkbench Jekyll Theme](/dataworkbench-jekyll-theme): theme for our GitHub pages, styling for other tools
- [DWb-developer](/dataworkbench-developer): portable tooling for developers (Docker image)

## Disclaimer

The documentation and the source repositories are a continuous work-in-progress,
they are not complete, and may be incorrect. We appreciate feedback, and
recommend to get in touch with questions and remarks.

We publish open source for some of our products.

Some of our work is in private repositories. This can be exploratory
work to investigate approaches or to develop proof-of-concepts, tooling that
is extremely tailored to our own setup and needs, or any other reason.

* Contact us [via the Data4Development website](https://data4development.nl/en/contact-us/)
* Or submit an issue or pull request via an appropriate Github repository.