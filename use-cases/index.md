---
title: Use cases
---

Developer-oriented use cases with pointers to further information.

## API access to public data validation reports

If the publisher identifier as used on the IATI Registry is known, it is possible to directly query the datasets for available reports. For instance, to get available reports for Oxfam Novib, use:

```.../iati-datasets/?filter[where][publisher]=onl```

Some of the datasets may contain the field ```discard: true``` and should be ignored. Unfortunately, Loopback does not offer a filter option to exclude these in the result set.

Next, the JSON version of the validation reports can be downloaded via

```...//iati-files/file/json/<md5>.json```

More information:

* The metadata formats are [documented in the API](/dataworkbench-api), and Postman collections are available to explore these.
* The validation report file formats such as the JSON data format are [documentd in the Validator](IATI-data-validator/formats/).

## Uploading and validating a file

TBC

## Using the IATI Rulesets on its own

The [IATI Rulesets](/IATI-Rulesets) are a collection of XSLT scripts, and can be run on their own. This makes it possible to use it in a local XML pipeline process.

This is still work in progress.

* The output of applying the rulesets currently is the original IATI file with embedded feedback messages.

TBC