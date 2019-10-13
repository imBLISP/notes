# HTTP

In addition to protocols that dictate how information is communicated from machine to machine and application to application (IP and TCP, respectively), it is frequently the case that the aplication itself has system of rules for how to interpret the data that was sent.

HTTP is one such example of an *application layer protocol*, which specifically dictates, the format by which clients <u>request</u> web pages from a server, and the format by which server <u>return</u> information to the clients.

Other application layer protocols include:

- File Transfer Protocol (FTP)
- Simple Mail Transfer Protocol (SMTP)
- Data Distribution Service (DDS)
- Remote Desktop Protocol (RDP)
- Extensible Message and Presence Protocol (XMPP)

Request:

```http
GET / HTTP/1.1
Host: cats.com
...
```

Response:

```http
HTTP/1.1 200 OK
Content-type: text/html
...
```

Request:

```http
GET /cats.html HTTP/1.1
Host: cats.com
...
```

Response:

```http
HTTP/1.1 404 Not Found
Content-type: text/html
...
```

A line of the form, `method request-target http-version`

Is a simple example of an *HTTP request line*, a crucial part of an overall HTTP request that a client may make to a server.

 `GET/POST request-target HTTP/1.1`

The host name (domain name of the server) is also included as a separate line of the overall HTTP request.

Taken together, the host name and the request target from the request line specify a specific resource being sought.

Based on whether the resource exists and whether the server is empowered to deliver that resource pursuant to the client's request, a *number of status* codes can result.

A status code is part of the first line that a server will use to respond to and HTTP request.

`http-version status`

|    Class     | Code | Text                  | Comments                                                     |
| :----------: | ---- | --------------------- | ------------------------------------------------------------ |
|   Success    | 200  | OK                    | All is well, valid request and response.                     |
| Redirection  | 301  | Moved Permanently     | Page is now at a new location, automatic redirects build in to most browsers. |
| Redirection  | 302  | Found                 | Page is now at a new location *temporarily*.                 |
| Client Error | 401  | Unauthorized          | Page typically requires login credentials.                   |
| Client Error | 403  | Forbidden             | Server will not allow this request.                          |
| Client Error | 404  | Not Found             | Server cannot find what was asked for.                       |
| Server Error | 500  | Internal Server Error | Generic Server failure in responding to the otherwise-valid request. |

