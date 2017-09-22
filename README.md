# Docker SureRoute
This container implements a minimal nginx server which serves only an [Akamai SureRoute](https://developer.akamai.com/learn/Optimization/SureRoute.html) object.
The object is served on `.well-known/akamai/sureroute.html`, all other paths respond with a 403 code.

This is intended to be used behind a proxy which redirects requests for this path for multiple applications to this server, removing the need for each application to ship a SureRoute object independently.

# Custom object
The object shipped with this image is downloaded from Akamai documentation pages. To use a custom object, derive from this Dockerfile and add your own object. For example:

```Dockerfile
FROM bonniernews/sureroute:latest
COPY my-custom-sureroute.html /usr/share/nginx/html/.well-known/akamai/sureroute.html
```