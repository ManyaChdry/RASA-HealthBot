Step 1: To use forms with Rasa Open Source you need to make sure that the Rule Policy is added to your policy configuration.  

    policies:
    - name: RulePolicy 
    
Step 2: **In the endpoints.yml, uncomment the action endpoint , to activate and use the action server**  
![image](https://user-images.githubusercontent.com/64036955/123055825-e8d2b900-d423-11eb-93e7-d63f78305ad6.png)

**_to define the forms_** : In actions.py file, we create a class for form activation and submission.  
**Define a form by adding it to the forms section in your domain, where slots are mentioned with type , name etc**    
**The name of the form is also the name of the action which you can use in stories or rules to handle form executions.**    
**We also need to define slot mappings for each slot which our form should fill. You can specify one or more slot mappings for each slot to be filled.**


### Activating a form:  
To activate a form, we need to add a story or rule, which describes when the assistant should run the form. 
Example: In case, the form is getting activated by an intent:  
![image](https://user-images.githubusercontent.com/64036955/123062679-613c7880-d42a-11eb-8726-5cf1b8645fd0.png)

### Deactivating a form: 
A form will automatically deactivate itself once all required slots are filled.  
We can describe your assistant's behavior for the end of a form with a rule or a story.   
If we don't add an applicable story or rule, the assistant will automatically listen for the next user message after the form is finished.  
(represented by active loop = NULL)


### Slot Mappings:  
There are 4 predefined mappings to fill the slots of a form based on the latest user message. We can have custom slot mappings too.  

➡️ Type 1 : from_entity  
This mapping fills slots based on extracted entities.  
 It will look for an entity called entity_name to fill a slot slot_name. If intent_name is None, the slot will be filled regardless of intent name. Otherwise, the slot will only be filled if the user's intent is intent_name.  
 If role_name and/or group_name are provided, the role/group label of the entity also needs to match the given values.The slot mapping will not apply if the intent of the message is excluded_intent. Note that you can also define lists of intents for the parameters intent and not_intent.    
 
 
 
 **Basic Syntax :**  
   
        forms:
          your_form:
            required_slots:
                slot_name:
                - type: from_entity
                  entity: entity_name
                  role: role_name
                  group: group name
                  intent: intent_name
                  not_intent: excluded_intent  
                  
❗In from_entity mapping, when an extracted entity uniquely maps onto a slot, the slot will be filled even if this slot wasn't requested by the form. The extracted entity will be ignored if the mapping is not unique. ❗    
(Roles and groups are yet in experiment phase only)

➡️ Type 2: from_text  
The from_text mapping will use the text of the next user utterance to fill the slot slot_name. If intent_name is None, the slot will be filled regardless of intent name. Otherwise, the slot will only be filled if the user's intent is intent_name.The slot mapping will not apply if the intent of the message is excluded_intent. Note that we can define lists of intents for the parameters intent and not_intent.  
**Basic Syntax :**  

        forms:
          your_form:
            required_slots:
                slot_name:
                - type: from_text
                  intent: intent_name
                  not_intent: excluded_intent
                  
➡️Type 3: from_intent :-
The from_intent mapping will fill slot slot_name with value my_value if user intent is intent_name or None. The slot mapping will not apply if the intent of the message is excluded_intent. Note that you can also define lists of intents for the parameters intent and not_intent.  
Note: The from_intent slot mapping will not apply during the initial activation of the form.
**Basic syntax :**

        forms:
          your_form:
            required_slots:
                slot_name:
                - type: from_intent
                  value: my_value
                  intent: intent_name
                  not_intent: excluded_intent
                  
➡️ Type 4: from_triggered_intent :
To fill a slot based on the intent that activated the form, we use the from_trigger_intent mapping.  
The from_trigger_intent mapping will fill slot slot_name with value my_value if the form was activated by a user message with intent intent_name. 
