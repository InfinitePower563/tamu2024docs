# API Routes
> Replace `financy_route` with the actual route
## How to Login
1. Submit a request to get a key
2. Use the key as the bearer for other routes
## Routes
> GET `http://financy_route/key`
>
*Headers:*
- None\
*Body:*
- Include password (as an SHA256 hash), username, and expiry as a unix timestamp.
- Formatted like: `user;hash;expiry`
\
*Returns*
- Bearer key in form `bearer_[number]`
- Both parts of the bearer key are required.
> POST `http://financy_route/transaction`
> 
*Headers:*
- Header `x-bearer`, containing the bearer key returned by the above route.\
*Body:*
- Include the name given for the transaction, and then the amount as a float.
- Formatted like: `name;amount`
> GET `http://financy_route/balance/<bearer>`
> 
\<bearer\>: The API token\
Returns: The balance for the user.
> GET `http://financy_route/transactions/<bearer>`
> 
\<bearer\>: The API token\
Returns: The total transactions for the user, separated by newlines.
Transactions are formatted like `unix timestamp:name:amount`