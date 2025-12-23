# Authentication

This system uses token-based authentication.

Steps:
1. Generate an API token.
2. Pass the token in the Authorization header.
3. Tokens expire after 24 hours.

If the token is missing or invalid, the API returns HTTP 401 Unauthorized.
