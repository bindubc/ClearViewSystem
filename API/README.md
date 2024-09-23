
### Authentication & Authorization API 
--- 
These endpoints handle user authentication, registration, and access control.
  *  __User Authentication__

      * __POST /auth/login__

        Description: Authenticates a user (Employer, Candidate, Admin) using credentials.

        Request Body: { "email": "string", "password": "string" }

        Response: JWT token
     * __POST /auth/register__:
        
        Description: Registers a new user (Employer, Candidate).
        
        Request Body: { "name": "string", "email": "string", "password": "string", "role": "employer/candidate" }
        
        Response: User profile with JWT token
     * __POST /auth/logout__:

         Description: Logs out the authenticated user.

         Headers: Authorization: Bearer token

         Response: 200 OK

     * __POST /auth/refresh-token__:
     
         Description: Refreshes the JWT token.

         Request Body: { "refreshToken": "string" }

         Response: New JWT token
