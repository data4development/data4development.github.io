---
title: Data model overview
---

## API data model overview

The system keeps its own metadata about publishers, datasets and files.

![](datamodel.drawio.svg)

* Information about publishers is taken from the IATI Registry. The **publishers** endpoint contains for instance the *slug* (identifier used on the Registry) and the *iati_id* (IATI organisation identifier).
* WIthin a publisher record, there is a list of **workspaces**. For the public IATI data there will be only one workspace, with the *slug* "public". The workspace id is a random unique identifier.

* Workspaces can have **versions**. For the public IATI data, there will only be one version. The workspace version contains information about the **datasets** for this publisher. Each dataset contains a single file and is identified by the md5 hash of the file.
* The dataset metadata contains information about the processing of the file and the associated publisher. Datasets may contain a field "discard: true" to indicate they are obsolete and will be removed during a cleaning cycle.
* The **validation report files** (when available) are stored using their md5 hash as the file name, and the type as file extension.

More information:

* The metadata formats are [documented in the API](/dataworkbench-api), and Postman collections are available to explore these.
* The validation report file formats such as the JSON data format are [documentd in the Validator](IATI-data-validator/formats/).