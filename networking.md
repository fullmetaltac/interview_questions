# Table of Contents
- [Table of Contents](#table-of-contents)
    - [HTTP(S)](#https)
    - [References:](#references)

### HTTP(S)

>🔹 ***Explain HTTP methods.***

The primary or most-commonly-used `HTTP` methods are `POST`, `GET`, `PUT`, `PATCH`, and `DELETE`. These correspond to create, read, update, and delete (or CRUD) operations, respectively. There are a number of other verbs, too, but are utilized less frequently. Of those less-frequent methods, `OPTIONS` and `HEAD` are used more often than others.

| HTTP     | CRUD           | Entire Collection (e.g. /users)                                                                        |
| -------- | -------------- | ------------------------------------------------------------------------------------------------------ |
| `GET`    | Read           | `200` (OK), list of users. Use pagination, sorting and filtering to navigate big lists.                |
| `POST`   | Create         | `201` (Created), Response contains response similar to GET /user/{id} containing new ID.               |
| `PUT`    | Update/Replace | `405` (Method Not Allowed), unless you want to update/replace every resource in the entire collection. |
| `PATCH`  | Update/Modify  | `405` (Method Not Allowed), unless you want to modify the collection itself.                           |
| `DELETE` | Delete         | `405` (Method Not Allowed), unless you want to delete the whole collection—not often desirable         |

> :bulb: *Status codes:*

HTTP response status codes indicate whether a specific HTTP request has been successfully completed. 

| range     | description                                                                                               |
| --------- | --------------------------------------------------------------------------------------------------------- |
| 100 – 199 | [Informational responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#information_responses) |
| 200 – 299 | [Successful responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#successful_responses)     |
| 300 – 399 | [Redirection messages](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#redirection_messages)     |
| 400 – 499 | [Client error responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#client_error_responses) |
| 500 – 599 | [Server error responses](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#server_error_responses) |

---

>🔹***What is Python http.server?***

Python http.server it’s a tool to share files over network.

```python
python -m http.server 9000
```
```shell
curl  -X GET http://127.0.0.1:9000/
# output is the list of current directory 
```

---

### References:

---