# @fayti1703/async-utils
Various async utility functions

#### slurp(stream, encoding)
* `stream` [<stream.Readable\>][stream_readable] The stream to slurp
* `encoding` [<string\>][string] The character encoding to use. All encodings supported by the node Buffer API are accepted. Use 'raw' to return the buffer itself. **Default: `'utf-8'`**
* Returns: [<Promise][Promise][<string\>][string]|[<Buffer\>][buffer][\>][Promise]

"Slurps" the given stream; all remaining data will be consumed and returned.

**Note:** This function rejects if the stream emits an `'error'` event.

#### request(options, body, encoding)
* `options` [<Object\>][object] | [<string\>][string] | [<URL\>][url] See [`https.request`](https://nodejs.org/api/https.html#https_https_request_options_callback)
* `body` [<string\>][string] | [<Buffer\>][buffer] The body of the request. Use `undefined` for no body.
* `encoding` [<string\>][string] The character encoding to use. Uses the same format as [`slurp`](#slurpstream-encoding)
* Returns: [<Promise][Promise][<Object\>][Object][\>][Promise] (See [`msgToObj`](#msgtoobjmessage))

Sends a HTTPS request to the specified server. The resulting response is passed to msgToObj, the result of which is returned.

#### requestInsecure(options, body, encoding)
* `options` [<Object\>][object] | [<string\>][string] | [<URL\>][url] See [`http.request`](https://nodejs.org/api/http.html#http_http_request_options_callback)
* `body` [<string\>][string] | [<Buffer\>][buffer] The body of the request. Use `undefined` for no body.
* `encoding` [<string\>][string] The character encoding to use. Uses the same format as [`slurp`](#slurpstream-encoding)
* Returns: [<Promise][Promise][<Object\>][Object][\>][Promise] (See [`msgToObj`](#msgtoobjmessage))

Sends a HTTP request to the specified server. This function acts just as [`request`](#requestoptions-body-encoding) does otherwise.

#### msgToObj(message)
* `message` [<http.IncomingMessage\>][http_incomingmessage] | [<http.ServerResponse>][http_serverresponse] The message to convert

Converts `message` into an equivalent object with an added `data` property and `toString` function.

**Note:** Due to the implementation of this function, properties from the message may be dropped. If this includes a property you need, please file a bug report.

#### sleep(ms)
* `ms` [<number\>][number] How long to sleep for

An alias for `setTimeout[util.promisify.custom]`.

[stream_readable]: https://nodejs.org/api/stream.html#stream_class_stream_readable
[string]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Data_structures#String_type
[buffer]: https://nodejs.org/api/buffer.html#buffer_class_buffer
[Object]: https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Object
[Promise]:https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise
[url]: https://nodejs.org/api/url.html#url_the_whatwg_url_api
[http_incomingmessage]: https://nodejs.org/api/http.html#http_class_http_incomingmessage
[http_serverresponse]: https://nodejs.org/api/http.html#http_class_http_serverresponse
