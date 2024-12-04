---
title: CursusEventParticipantDownload
---

This snippet downloads the participants of a Cursus event.

## Properties

It uses the following snippet properties:

| Property | Description                                                                            | Default         |
|----------|----------------------------------------------------------------------------------------|-----------------|
| event    | ID of the events whose participants are downloaded.                                    | -               |
| sortby   | Field name according to which the downloaded participants are sorted.                  | lastname        |
| sortdir  | Direction in which the downloaded participants are sorted.                             | ASC             |
| status   | Comma separated list of event participant status to filter the downloaded participants | reserved,booked |

The download will be created according to the documentation on the
[Export](../08_Export.md) page.
