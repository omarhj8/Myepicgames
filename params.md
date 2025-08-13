# Params 
### visible to other users 

- `id`: the unique identifier of the account
- `displayName`: the current display name of the account
- `externalAuths`: a list of external auths (e.g. `xbl`, `psn`, `nintendo`)
----------------------------------------------------------------------------
### Auth intreface
- `grant_type`:	The grant type being used: authorization_code, client_credentials, exchange_code, password, or refresh_token. 
- `deployment_id`:	The deployment ID that the client is trying to authenticate with
- `scope`:	 (permissions) that will be requested from the user. For example: basic profile, friends_list, and presence
- `code`:	The authorization code received from the authorization server
- `client_id`:	The OAuth Client ID for your application.
- `client_secret`:	The OAuth Client Secret for your application.
- `exchange_code`:	The exchange code passed by Launcher to the game client; only used with the exchange_code grant type.
- `username`:	The username (email address) for the account; only used with the password grant type.
- `password`:	The password for the account; only used with the password grant type.
- `refresh_token`:	The refresh token passed by Launcher to the game client; only used with the refresh_token grant type.\
  
for example
```http
POST /epic/oauth/v2/token HTTP/1.1
Host: api.epicgames.dev
Content-Type: application/x-www-form-urlencoded
Authorization: Basic Zm9vOmJhcg==

grant_type=password&
deployment_id=foo&
scope=basic_profile friends_list presence&
username=user@example.com&
password=s3cr3t
```
and the response 
```json
{
  "scope": "basic_profile friends_list presence",
  "token_type": "bearer",
  "access_token": "eyJ0IjT3hFandibjdrZ1hIsImlSXq3Vw",
  "refresh_token": "eyJ0IjoiZXBpkQ",
  "expires_in": 7200,
  "expires_at": "2020-04-30T22:34:43.549Z",
  "refresh_expires_in": 28800,
  "refresh_expires_at": "2020-05-01T04:34:43.549Z",
  "account_id": "9626f441055349ce8cb7d7d5a483eaa2",
  "client_id": "xyza7891lhxMVYGCON7LgnKZZ8HQGD5H",
  "application_id": "fghi4567O03HROxEjwbn7kgXpBhnhWwv"
}
```
- `access_token`:	The access token, which may optionally have a prefix (for example: eg1~[token]). This value should be passed as is in the Authorization header using the Bearer type on any requests to Epic services
- `account_id`:	The Epic Account ID for the user that the token was generated for
- `client_id`:	The Client ID which was used to generate this token.
- `application_id`:	The Application ID which the Client is associated with.
- `token_type`	The type of token generated; value will always be bearer.

