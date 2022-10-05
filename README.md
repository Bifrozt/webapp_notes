# webapp_notes
Web application testing notes.

## Request headers

#### X-Forwarded-For
Used to identify the originating IP of a client that passed trough a proxy server.

##### I.E.
- Client external IP: 11.22.33.44
- Proxy external IP: 55.66.77.88

In the above example, the server would understand **55.66.77.88** to be the **Client IP**.
If the proxy server appends the **X-Forwarded-For** header to the request, 
it allows the server to get the "real" Client IP from that header

X-Forwarded-For: 11.22.33.44
    
