GATT defines a few procedures for discovering the services from a GATT database located on a GATT Server. These procedures rely on Attribute Protocol (ATT) operations.

 

One of those procedures is the Discover All Primary Services, which uses ATT’s Read By Group Type request/response.

The parameters for this request are:

- The starting and the ending handle for the search.
- The attribute type which is the UUID searched for.
 

In order to discover all primary services, you need to set the starting handle to 0x0001, the ending handle to 0xFFFF (these are the minimum and maximum values for attribute handles, so the search will be performed over the entire database) and the attribute type to 0x2800, which is the UUID for the <<Primary Service>> declaration.

 

The response from the Server will include a list of tuples corresponding to found services, each tuple consisting of:

- The attribute handle where the requested declaration was found (where UUID is equal to 0x2800)
- The so-called end-group handle – the last attribute handle before a new similar declaration is found, basically the last attribute that belongs to this service
- The attribute value of the declaration; this is the service UUID of the found service (the service type, e.g. Heart Rate Service); it may be a 16-bit, a 32-bit or a 128-bit UUID
 

The end-group handle is useful for two things.

One is to know the borders of each service, i.e. not only where it starts, but also where it ends. Keep in mind that attribute handles are not necessarily consecutive, so the start of a new service may very well not be equal to the end of the previous service plus one.

The other use is that obviously not all services can be sent in a single response if there are many services on the Server. The Server only sends as many as it can fit in the ATT packet. So the Client must continue the search, but for the next request he will not set the starting handle parameter to 0x0001, but instead it will set it to the last end-group handle from the previous response, plus one.

 

For example, let’s say the Server has this database structure (UUIDs are purely fictional):

- Service 1: from 0x0001 to 0x0004, value (16-bit service UUID) = 0x1234
- Service 2: from 0x0006 to 0x0009, value (16-bit service UUID) = 0x5678
- Service 3: from 0x0010 to 0x0018, value (128-bit service UUID) = 0x1234567890abcdef1234567890abcdef
- Service 4: from 0x0020 to 0x0030, value (16-bit service UUID) = 0x2345
 

After the first request (0x0001-0xFFFF), the Read By Group Type response will include these bytes, in order (LSB first):

- 0x01, 0x00 (handle of start of service), 0x04, 0x00 (end-group handle), 0x34, 0x12 (UUID), 0x06, 0x00, 0x09, 0x00, 0x78, 0x56
The next service type is a 128-bit UUID, so the Server cannot include it in the response and it stops after the first two services.

 

The Client, upon seeing that the last service in this list ended at 0x0009, proceeds to sending a new Read By Group Type request with this handle range: 0x0010-0xFFFF.

The response will only include Service 3, so the Client will need to issue a third request with the range: 0x0019-0xFFFF.

After the third response, the Client will continue with a 4th request, with the range: 0x0031-0xFFFF. This time, it will get an Error Response with message “Attribute Not Found”.

Thus, it can safely conclude that Primary Service Discovery is complete.

 

See Bluetooth Core 4.1 specification, vol. 3, section 4.4.1 for more details and examples.
