---
description: Learn what batch processing is and how it works.
---

# Batch processing

Many integration scenarios require the processing of large amounts of data. Retrieving all the data at once is highly inefficient or even impracticable, which can burst your pipeline's memory.

In this case, it is best to process the data continuously and in a controlled manner in smaller batches, which is exactly the concept of batch processing.

Currently the Digibee Integration Platform has five components that natively support this strategy:&#x20;

* [Stream DB](https://docs.digibee.com/documentation/components/structured-data/stream-db-v1) (Deprecated)
* [Stream DB V3](https://docs.digibee.com/documentation/components/structured-data/stream-db-v3)
* [Stream Excel](https://docs.digibee.com/documentation/components/files/stream-excel)
* [Stream File Reader](https://docs.digibee.com/documentation/components/files/stream-file-reader)
* [For Each](https://docs.digibee.com/documentation/components/logic/for-each)
