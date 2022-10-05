# webapp_notes
Web application testing notes.

# Request headers

### [X-Forwarded-For](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Forwarded-For)
Used to identify the originating IP of a client that passed trough a proxy server.

#### I.E.
- Client external IP: 11.22.33.44
- Proxy external IP: 55.66.77.88

In the above example, the server would understand **55.66.77.88** to be the **Client IP**.
If the proxy server appends the **X-Forwarded-For** header to the request, 
it allows the server to get the "real" Client IP from that header

```
X-Forwarded-For: 11.22.33.44
```

#### The concern
Under a lot of conditions, it's possible to spoof the Client IP trough the use of **X-Forwarded-For**.
Without being behind a proxy server, it's possible to add this header to the requests before sending 
it to the server. If the server/application that uses this header to identify "misbehaving" clients
and impose restrictions (set bandwidth/request limits, temp/permanent banning IP etc).


Changing this
```
X-Forwarded-For: 11.22.33.44
```
to this
```
X-Forwarded-For: 19.28.37.46
```
would be a very trivial way to spoof one's IP address.
