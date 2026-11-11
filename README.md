# Document AI

The common document-AI vocabulary -- the extraction jobs that read a document, the parsers or extractors that define what to read, and the fields and tables they return -- distilled from the APIs that already exist. Stored files belong to the files context. Part of [Schema Commons](https://github.com/api-commons/schema-commons),
published by the [API Commons](https://apicommons.org).

Built from the providers tagged Document AI, OCR, Data Extraction, Document Processing, Intelligent Document Processing, IDP, PDF, Document Parsing in [APIs.io](https://apis.io) that
publish their own OpenAPI. Only harvested contracts count -- nothing API Evangelist
generated. Every number below is a count of providers.

## What the market already agrees on

<!-- commons:summary -->
| Concept | Expose it | Readable schema | Core properties (share) | Collection named |
| --- | ---: | ---: | --- | --- |
| extraction | 35 | 33 | id 55%, status 52% | extract 25, parse 10, ocr 5, extractions 5 |
| extractor | 2 | 2 |  | extractors 1, processors 1, document_types 1 |

Cohort: 132 providers with harvested OpenAPI, 35 crosswalks. Of the providers exposing a extraction: 91% create, 29% list, 20% fetch, 3% update, 3% delete. Generated 2026-11-11 by build.py.
<!-- /commons:summary -->

Shares are of the providers with a readable resource schema for that concept. The
extended tier and the long tail of every concept are in [profile.yml](profile.yml).

## What the measurement shows

- An extraction agrees only on id and status. What comes back -- key-value fields, tables, markdown, entities, a JSON object shaped by a schema -- is each product's own model; document AI shares the job, not the result.
- Extractors (parsers, processors, document types) are a resource at only a few providers; most take the schema inline with each extraction request.

## Artifacts

- [openapi.yml](openapi.yml) -- OpenAPI 3.1 of the shared operations. No one serves it; it
  is the shape to map to. Lints clean against the
  [naming ruleset](https://github.com/api-commons/schema-commons/blob/main/ruleset/schema-commons-naming.yaml).
- [schema/](schema) -- JSON Schema 2020-12 per concept; each property carries
  `x-commons-tier`, `x-commons-share`, `x-commons-providers` and the spellings seen.
- [crosswalk/](crosswalk) -- one per provider, common name -> their name, with the harvested
  spec and operations each mapping was read from.
- [adopters.yml](adopters.yml) -- who exposes which concept, linked to their APIs.io page.
- [concepts.yml](concepts.yml) -- the only hand-written input: concepts, path segments and
  their qualifiers, aliases, reviewed exclusions, merged duplicates, and the decisions below.
- [census/](census) -- the cohort and the raw census the profile is built from.

## Decisions

These are calls, not measurements, recorded so they can be revisited as the method matures.

- An extraction covers OCR, parse, extract and analyze operations, and jobs or predictions beneath a document or parser path.
- Extractors cover parsers, processors, document types and extraction templates, at `/extractors`.
- Web-page extraction (Diffbot) is not document AI and is excluded; a web-scraping context would own it.
- Duplicates merged: Nitro, Sensible.

## Rebuild

```bash
../schema-commons/scripts/run.sh .
```

## License

Artifacts CC BY-NC-SA 4.0 ([LICENSE](LICENSE)); code Apache 2.0 ([LICENSE-CODE](LICENSE-CODE)).
