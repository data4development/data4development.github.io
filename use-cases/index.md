---
title: Use cases
---

Developer-oriented use cases with pointers to further information.

## API access to public data validation reports

If the publisher identifier as used on the IATI Registry is known, it is possible to directly query the datasets for available reports. For instance, to get available reports for Oxfam Novib, use either:

```http
.../iati-datasets/?filter[where][publisher]=onl
```

Or use the JSON query

```json
{"where": {"publisher": "onl"}}
```

In urlencoded form this looks like:

```http
.../iati-datasets/?filter=%7B%22where%22%3A%20%7B%22publisher%22%3A%20%22onl%22%7D%7D
```

Some of the datasets may contain the field ```discard: true``` and should be ignored: they will be removed by a periodic garbage collection process. To filter them out, use a JSON query:

```json
{
  "where": {
    "and": [
      {"publisher": "onl"},
      {"discard": {"exists": false}}
    ]
  }
}
```

In urlencoded form this is:

```http
.../iati-datasets/?filter=%7B%22where%22%3A%20%7B%22and%22%3A%20%5B%7B%22publisher%22%3A%20%22onl%22%7D%2C%20%7B%22discard%22%3A%20%7B%22exists%22%3Afalse%7D%7D%5D%7D%7D
```

Next, the JSON version of the validation reports can be downloaded via

```.../iati-files/file/json/<md5>.json```

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

