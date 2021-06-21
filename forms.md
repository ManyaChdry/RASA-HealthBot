To use forms with Rasa Open Source you need to make sure that the Rule Policy is added to your policy configuration.  

    policies:
    - name: RulePolicy 
    
    
**Define a form by adding it to the forms section in your domain.**  
**The name of the form is also the name of the action which you can use in stories or rules to handle form executions. **  
**ou also need to define slot mappings for each slot which your form should fill. You can specify one or more slot mappings for each slot to be filled.**
