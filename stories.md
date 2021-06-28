### Stories
Stories are a type of training data used to train your assistant's dialogue management model.
Stories can be used to train models that are able to generalize to unseen conversation paths.

#### Format
A story is a representation of a conversation between a user and an AI assistant, converted into a specific format
where user inputs are expressed as intents (and entities when necessary), while the assistant's responses and actions are expressed as action names.

![Stories](https://user-images.githubusercontent.com/72215893/123614208-bf4dcf00-d821-11eb-8efd-56f0fd7d48c6.png)

### Actions
All actions executed by the bot, including responses are listed in stories under the **action key.** <br>
You can use a response from your domain as an action by listing it as one in a story. 
Similarly, you can indicate that a story should call a custom action by including the name of the custom action from the actions list in your domain.<br>

### Events
During training, Rasa Open Source does not call the action server.<br>
Because of this, events such as setting a slot or activating/deactivating a form have to be explicitly written out as part of the stories

### Form Events 
There are three kinds of events that need to be kept in mind while dealing with forms in stories.<br>
-  A form action event **(e.g. - action: restaurant_form)** is used in the beginning when first starting a form, and also while resuming the form action when the form is already active.
-  A form activation event **(e.g. - active_loop: restaurant_form)** is used right after the first form action event.
-  A form deactivation event **(e.g. - active_loop: null)**, which is used to deactivate the form.
-  
### Or Statements
Another way to write shorter stories, or to handle multiple intents the same way, is to use an or statement. <br>
For example, if you ask the user to confirm something, and you want to treat the affirm and thankyou intents in the same way. 
The story below will be converted into two stories at training time:<br>
![OR](https://user-images.githubusercontent.com/72215893/123616729-31bfae80-d824-11eb-8ded-0353ef2a5788.png)
