Domain file contains entries for all of the things that your assistant can recognize.

So, list all the intents, actions, responses, and more.

So, if you create any new intent in the nlu file that has to be listed in the domain file under the intent section.

Response template should also be added for each intent, this way the assistant will know what ot say back when someone asks one of the questions for the pre-defined intent.
In this file, we also define what will our bot do when a new intent is added or defined.

EG: when it detects ask_eat_unheathy intent, this means the user has a question about healthy diets, we want the user to reply with a template that we previously defined in the end of yaml file.
