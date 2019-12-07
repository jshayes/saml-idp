# Dependencies
This requiers docker to work.

Install [Docker for Mac](https://docs.docker.com/docker-for-mac/install/). This should include `docker-compose`.

# Setup
First, clone the repo locally and cd into the directory.

The, create the `.env` file
```
cp .env.example .env
```

| Variable      | Description                                                                                                                                                                      |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| IDP_HOST      | The hostname of the IDP. This defaults to `localhost`. The SAML IDP will be available on `http://$IDP_HOST:8080`. So, by default it will be available on `http://localhost:8080` |
| SP_ENTITY_ID  | The Service Provider's entity ID.                                                                                                                                                |
| SP_ACS_URL    | The Service Provider's Assertion Consumer Service URL.                                                                                                                           |
| SP_LOGOUT_URL | The Service Provider's Single Logout Service URL.                                                                                                                                |

Once the environment is configured, you can start the IDP by doing
```
docker-compose up -d
```

You can then get the IDP's metadata [here](http://localhost:8080/simplesaml/saml2/idp/metadata.php?output=xhtml).

Configure the SP for this IDP, and then you should be able to test login.

# Testing

By default, there are two users that you can sign in as.

| Username | Password  | UID | Email Address     | First Name | Last Name |
| -------- | --------- | --- | ----------------- | ---------- | --------- |
| user1    | user1pass | 1   | user1@example.com | User       | One       |
| user2    | user2pass | 2   | user2@example.com | User       | Two       |

You can modify the users, or add new ones by modifyign the `authsources.php` file.
