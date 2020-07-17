# Newsletter Signup

The newsletter signup allows for signing up people for a newsletter. No sending of e-mail of managing subscriber status is done after signing up.
```
{
  "config": {
    "newslettersignup": {
      "isActive": true
    }
  }
}
```



## Endpoints

| Route                                      | Description                                                  |
| ------------------------------------------ | ------------------------------------------------------------ |
| `GET /api/site/:SITE_ID/newslettersignup`  | List all newsletter signups for a site<br/>Query params: confirmed. Only available for moderators |
| `POST /api/site/:SITE_ID/newslettersignup` | Create a newslettersignup                                    |





## Signup confirm (beta)

There is the possibility to send an e-mail and let the user confirm the signup. This is however in Beta and currently not active used.

`POST /api/site/:SITE_ID/confirm`

Payload:

```
{
  "confirmToken": "TOKEN"
}
```

