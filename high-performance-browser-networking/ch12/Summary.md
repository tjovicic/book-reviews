# HTTP2

# Benefits 
- request and response multiplexing, compression of HTTP header fields, request prioritization

# Binary framing layer
- the way HTTP verbs, methods, headers are encoded in transit is different 
- all HTTP/2 communication is split into smaller messages and frames, encoded in a binary format

## Stream, message, frame
- single TCP connection can carry any number of bidirectional streams
- stream has a unique identifier and carries messages
- message is a logical HTTP message and consists of frames
- ability to break down HTTP message into frames, interleave then and then reassemble them on the other end

## Server push
- server can send multiple responses for a single client request
