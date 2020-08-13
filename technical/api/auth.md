# Authentication and Authorization

## Login route

Login is dan per site:

```GET /oauth/site/:SITE_ID/login```

The user is then send to the authentication server with oAuth clientId set in the siteConfig. And is authenticated throught the oAuth 2.0 protocol.

After successfull authentication the Api redirects back to the Frontend / CMS with a JWT token in the url that the frontend server can use for authenticating requests.

Like so:

```X-Authorization: Bearer JWT```

Named `X-Authorization` so it won't collide with Basic Authenications headers.

Following urls can be used to get user info with the JWT token.

```GET /oauth/site/:SITE_ID/me```

SiteID is not necessary, since userId is present in JWT, but for consistency sake is used