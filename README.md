# Good public api
## Documentation
  - Interactive
  - Versioned
  - Accept user feedback
  - OpenAPI document
## Versioning
  - Prefix endpoints with version ex. /v1/events
  - Expose a version endpoint to show updates to users and keep client versions up to date with the api
  - GRPC allows client/server code to be generated in many different languages. So you could have one server and many different client code implementations that stay up to date by simply running the generate command.
## Naming
    - Use plural nouns for endpoints
        - /v1/events/:id
        - /v1/events/:id/survey/:id
    - Don’t use verbs in endpoints, the verbs for http should be enough to describe behavior
        - POST /v1/events creates an event
        - PUT /v1/events updates
        - DELETE /v1/events/:id deletes
## Errors
    -  should make sense to people
    -  uniform response
    - http error codes go with the error response
        - Malformed request 400 plus error message
## Auth
    - JWT tokens
    - Signed with expirations
    - Verify signature on server side
    - Refresh tokens
    - Third party? Use google 0auth
## Monitoring
    - Prometheus and Grafana
    - Expose a metrics endpoint that can be scrapped by prometheus
    - Generate dashboards by creating queries for the prometheus data
    - Profile application to find memory leeks or long running go routines
    - Instrument APM
## Updates
    - Make additions
    - Continue supporting old clients and integrations
    - Feedback from customers
    - Atomic updates when all api and client changes are made at once
    - Or slowly implement new api and old api is just calls to new api
## CICD
    - Setup circle ci or something similar to automate tests and building docker/container images
    - Automate tagging of images with branch-{git hash} + date?
    - Canary deployments to run a small set of users on the new code
    - Feature flags, environment vars enable features
## Kubernetes
    - Developers should feel empowered to deploy things
## Code can always be less complicated
    - Should be easy to read
