# 4. Encoding

- the biggest problem: keeping backward and forward compatibility

## Formats
- encoding: translation from an in-memory representation to a byte sequence (serialization, marshalling)

## JSON and XML
- problem with dealing with large numbers, floating points in JSON
- poor support for schemas in JSON
- XML is too verbose

## Binary encoding
- MessagePack(with schema encoded), Protobuf, Trift (using field numbers)
- keeping forward and backward compatibility using tag numbers and offsets
- Avro has no field tags, uses readers and writers schema

## Web services
- SOAP vs JSON
  - although standardized and doesn't rely on HTTP, SOAP has issues with interoperability and ease of use

### RPC
- depends on the network which can be buggy
- when timeouts happen you don't know what happened
- difficult to achieve interoperability between multiple languages
- usually used inside an organization, JSON for outside traffic

### Message brokers
- provides separation between producer and consumer
- challenging to support responses from consumer
