## Rasa Open Source HTTP API :
You can use the HTTP API to interact with a running Rasa Open Source server. With the API, you can train models, send messages, run tests, and more.  

### Enabling the HTTP API
**By default, running a Rasa server does not enable the API endpoints.**  
Interactions with the bot can happen over the exposed webhooks/<channel>/webhook endpoints.  
To enable the API for direct interaction with conversation trackers and other bot endpoints, add the --enable-api parameter to your run command.  
  
      rasa run --enable-api
  
  By default, the HTTP server runs as a single process. You can **change the number of worker processes using the SANIC_WORKERS environment variable.**  
  It is recommended that you set the number of workers to the number of available CPU cores
