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
  in the first command we are requesting an url to ask for the data from airtable api.<br>

### Writing Custom Actions
  
  **The Action class is the base class for any custom action. To define a custom action, create a subclass of the Action class and overwrite the two required methods, name and run. The action server will call an action according to the return value of its name method when it receives a request to run an action**
  ![2021-07-01 15_23_35-Actions](https://user-images.githubusercontent.com/72215893/124105011-6fb90e80-da80-11eb-9cee-c57bfe99a6cf.png)
  
  #### Methods
  - **Action.name** -Defines the action's name. The name returned by this method is the one used in your bot's domain. It returns Name of action.<br>
      **Return type: str**<br>
  - **Action.run** - 


   ![Actions run](https://user-images.githubusercontent.com/72215893/124113447-13a6b800-da89-11eb-9bb8-83c1eeee1aba.png)
   
   **A dispatcher is an instance of the CollectingDispatcher class used to generate responses to send back to the user.**<br>
   **CollectingDispatcher** has one method, utter_message, and one attribute, messages. 
   It is used in an action's run method to add responses to the payload returned to the Rasa server<br>
   
   #### CollectingDispatcher.utter_message
   **The utter_message method can be used to return any type of response to the user:**<br>
    **text- The text to return to the user.**<br>
    It can be a image 'url' , response etc<br>
    Example: dispatcher.utter_message(response = "utter_greet")<br>
     dispatcher.utter_message("Thanks, your answers have been recorded!")
     
     
 ### Tracker
The Tracker class represents a Rasa conversation tracker. It lets you access your bot's memory in your custom actions. You can get information about past events and the current state of the conversation through Tracker attributes and methods.

### Header 
It specifies the content type that is json format
 

