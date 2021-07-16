Domain file contains entries for all of the things that your assistant can recognize.  
The domain defines the universe in which your assistant operates. It specifies the intents, entities, slots, responses, forms, and actions your bot should know about. It also defines a configuration for conversation sessions.  


Keywords used:   
- version
- intents : Lists all intents used in your NLU data.
-  entities: Lists all entities that can be extracted.
-   responses:  Responses are messages that your assistant sends to the user. A response is usually only text, but can also include content like images etc . Each response name should start with utter_.  
Note: We can add multiple response lines as well.  Rasa will randomly pick one of the two response variations to use! We can add images to a response by providing a URL to the image under the image key:  
image: <image_url>    
-   slot: It is the memory of bot.
-   actions: For listing the custom actions.


If we create any new intent in the nlu file that has to be listed in the domain file under the intent section. All intents used in nlu file, must be mentioneed here.

Response template should also be added for each intent, this way the assistant will know what ot say back when someone asks one of the questions for the pre-defined intent.
In this file, we also define what will our bot do when a new intent is added or defined.

Session configuration: 
- Conversation Session :  Dialogue between the assistant and the user. It can start in any of the 3 ways:  
1. the user begins the conversation with the assistant,
1. the user sends their first message after a configurable period of inactivity, or
1. a manual session start is triggered with the /session_start intent message.

- We can define the period of inactivity after which a new conversation session is triggered in the domain under the session_config key.  
Parameters for session_config key: -

session_expiration_time: defines the time of inactivity in minutes after which a new session will begin.
carry_over_slots_to_new_session: determines whether existing set slots should be carried over to new sessions.
