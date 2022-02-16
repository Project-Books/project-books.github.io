With the HTTP verb set as `POST`, connect to `localhost:8080/login`. In the body of the request, have the following raw JSON:

```json
{
    "username": "user@user.user",
    "password": "password"
}
```

![image](https://user-images.githubusercontent.com/11173328/110239332-4b1fb080-7f3e-11eb-85c8-54a375dc38c9.png)

You'll get back a header that contains a JWT token. For any requests that require authentication (currently all apart from logging in, logging out and registering), you will need to pass this token in so that the server knows it can trust you as it has already authenticated you.
