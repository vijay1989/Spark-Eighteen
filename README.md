
problem

Write a server which can generate and assign random tokens within a pool and release them after some time. Following endpoints should work on your server:


1. Endpoint to generate unique token in the pool.

2. Endpoint to assign unique token. On hitting this endpoint, server should assign available random token from the pool and should not serve the same token again until it's freed or unblocked. If no free token is available in pool, it should serve 404.

3. Endpoint to unblock the token in the pool. Unblocked token can then be served in (2)

4. Endpoint to delete the token in the pool. Deleted token should be removed from the pool.

5. Endpoint to keep the tokens alive. All tokens should receive this endpoint within 5 minutes. If a token doesn't receive a keep-alive in last 5 mins, it should be deleted from pool and should not be served again.

6. By default each token will be freed/released automatically after 60s of use. To keep the token allocated to himself, client should request keep-alive (5) on same token within 60s.

Enforcement: No operation should result in iteration of whole set of tokens; i.e, complexity cannot be O(n).

Please deploy the same on Heroku and also share the postman collection of all those apis.

====================================================================================================================

how to use -

create virtual env
Activate the virtual environment: source venv/bin/activate
move into django_auth dir and run below command
pip install -r requirements.txt


---------------------- createsuper user or you can login with below detail ------------

admin@gmail.com
admin singh
pass - SPOC_2020

================================================================================================================
postman collection

method  - post
http://127.0.0.1:8000/user/create/
{
    "email": "test9@gmail.com",
    "first_name": "test9",
    "last_name":"spark",
    "password":"dgsd"
}

method  - post
http://127.0.0.1:8000/user/obtain_token/
{
    "email": "test9@gmail.com",
    "password":"dgsd"
}

method  - get
http://127.0.0.1:8000/user/get_user_detail/

in header use - Content-Type,Authorization

Note -  For more detail with images check doc_imgs dir
