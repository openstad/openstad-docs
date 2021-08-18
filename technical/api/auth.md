# Authentication and Authorization

## Login route

Login is done per site.

```GET /oauth/site/:SITE_ID/login```

The user is then send to the authentication server with oAuth clientId set in the siteConfig. And is authenticated through the oAuth 2.0 protocol by the auth server.

After successful authentication the Api redirects back to the Frontend / CMS with a JWT token in the url that the frontend server can use for authenticating requests.

Like so:

```X-Authorization: Bearer JWT```

Named `X-Authorization` so it won't collide with Basic Authentications headers.

Following urls can be used to get user info with the JWT token.

```GET /oauth/site/:SITE_ID/me```

