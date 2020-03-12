---
title: Use cases
---

Developer-oriented use cases with pointers to further information.

## API access to public data validation reports

### Finding available datasets

If the publisher identifier as used on the IATI Registry is known, it is possible to directly query the datasets for available reports. For instance, to get available reports for Oxfam Novib, use either:

```http
https://.../api/v1/iati-datasets/?filter[where][publisher]=onl
```

Or use the JSON query

```json
{"where": {"publisher": "onl"}}
```

In urlencoded form this looks like:

```http
https://.../api/v1/iati-datasets/?filter=%7B%22where%22%3A%20%7B%22publisher%22%3A%20%22onl%22%7D%7D
```

The result will be in the form of an array of objects with dataset informtion:

```json
[
  {
    "id": "00349e0d-9be2-49f1-be5b-3c3dab35e5de",
    "name": "undp/undp-moz.xml",
    "url": "http://open.undp.org/download/iati_xml/Mozambique_projects.xml",
    "md5": "ccd539adad7d0caa2d362d125c1b2f4a",
    "publisher": "undp",
    "filename": "undp-moz.xml",
    "downloaded": "2020-03-12T11:00:35.000Z",
    "updated": "2020-03-12T11:33:16.000Z",
    "feedback-updated": "2020-03-12T11:34:13.000Z",
    "svrl-updated": "2020-03-12T11:34:49.000Z",
    "json-updated": "2020-03-12T11:34:34.000Z",
    "is-xml": true,
    "size": "697544",
    "processing": "2020-03-12T11:33:19+00:00",
    "file-type": "iati-file",
    "iati-version": "2.03",
    "feedback-version": "1.0-beta-8",
    "json-version": "1.0-beta-8",
    "svrl-version": "1.0-beta-8"
  },
    ... (etc)
```

The field `json-updated` indicates if (when) a JSON report has been generated.

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
https://.../api/v1/iati-datasets/?filter=%7B%22where%22%3A%20%7B%22and%22%3A%20%5B%7B%22publisher%22%3A%20%22onl%22%7D%2C%20%7B%22discard%22%3A%20%7B%22exists%22%3Afalse%7D%7D%5D%7D%7D
```

### Retrieving validation reports in JSON format

Next, the JSON version of the validation reports can be downloaded via 

```http
https://.../api/v1/iati-files/file/json/<md5>.json
```

The result will be in the form

```json
{
  "schemaVersion": "1.0-beta-8",
  "iatiVersion": "2.03",
  "summary": {
    "critical": 0,
    "danger": 3,
    "warning": 5,
    "info": 0,
    "success": 0
  },
  "filetype": "iati-activities",
  "validation": "ok",
  "feedback": [],
  "activities": [
    {
... etc
```

The `summary` field gives a count of types of feedback messages included. The `activities` field is an array with feedback messages organised per activity.

### More information:

* The metadata formats are [documented in the API](/dataworkbench-api), and Postman collections are available to explore these.
* The validation report file JSON format is [documented in the Validator](/IATI-data-validator/formats/json/).

## Uploading and validating a file

TBC

## Using the IATI Rulesets on its own

The [IATI Rulesets](/IATI-Rulesets) are a collection of XSLT scripts, and can be run on their own. This makes it possible to use it in a local XML pipeline process.

This is still work in progress.

* The output of applying the rulesets currently is the original IATI file with embedded feedback messages.

TBC

