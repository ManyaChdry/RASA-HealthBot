A custom action can perform any action that we want and can run any code that we want : <br>
  It can be enabling an API , database queries , interact with any kind of external source , validate <br>
  **In custom actions will take the slot values collected by the form and send a request to the Airtable API to post the data to the spreadsheet** <br>
  
  Custom actions are written in actions.py file.<br>
  
 **There are two ways to run the action server, depending on whether you are using an environment with rasa installed or not:
If rasa is installed, you can run the action server using a rasa command** <br>
  Rasa run actions <br>
  Custom actions run on a different server, when we are working on an assistant that uses custom actions, we run two servers : one for rasa open source other for custom actions<br>
  
  #### load_dotenv()
  **Environment Variables are string variables containing information that an operating system uses to control services and applications.
   Environment variables help applications to know what directory to install files in, where to store temporary files, or where to find the user profile information.**
  Environment variables are an important part of all projects, passing configuration settings, connection strings, etc, from local to production environments.<br>
  Dotenv is a zero-dependency module that loads environment variables from a.env file into process.env. 
  Storing configuration in the environment separate from code is based on The Twelve-Factor App methodology.
  
  ### create_health_log()
  it takes all the slots as arguements.<br>
  in the first command we are requesting an url to ask for the data from airtable api.
