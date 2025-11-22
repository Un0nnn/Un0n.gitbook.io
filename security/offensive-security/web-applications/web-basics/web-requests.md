# Web Requests

#### **GET vs POST**

GET requests are used for actions like searches or page access, while POST requests are used when transferring files or hiding parameters from the URL.

**Key differences:**

* **POST puts data in the request body**, GET in the URL.
* **Benefits:**
  1. **No logging issues:** Large uploads aren’t stored in logs like GET URLs.
  2. **Less encoding:** POST can send binary data; only separators need encoding.
  3. **More data:** POST isn’t limited by URL length (URLs usually < 2000 chars).

#### **CRUD API**

Not API's are the same technically, but the principles used are the same like in REST APIs.

{% code title="CREATE" %}
```shellscript
curl -X POST http://<SERVER_IP>:<PORT>/endpoint.php/library/ -d '{"book_name":"NEW_BOOK", "author_name":"AUTHOR_NAME"}' -H 'Content-Type: application/json'
```
{% endcode %}

{% code title="READ" %}
```shellscript
curl http://<SERVER_IP>:<PORT>/endpoint.php/library/book | jq # Retrieve specific entries
```
{% endcode %}

{% code title="UPDATE (PUT)" %}
```shellscript
curl -X PUT http://<SERVER_IP>:<PORT>/endpoint.php/library/book -d '{"book_name":"NEW_BOOK", "author_name":"AUTHOR_NAME"}' -H 'Content-Type: application/json'
```
{% endcode %}

`PATCH` is used to partially update an entry ("e.g. author\_name"), while `PUT` is used to update the entire entry.

{% code title="DELETE" %}
```shellscript
curl -X DELETE http://<SERVER_IP>:<PORT>/endpoint.php/library/book # Will delete entire entry
```
{% endcode %}
