## System Architecture
Our payment system leverages service plan management and user management for service providers.
The system implements the following:

 - configurable services and service plans for a provider;
 - configurable user types for a provider;
 - standard user flows based on your subscription model (individual users, companies);
 - standard user verification procedures applied to all users of the same type ( **Know your customer** procedure);
 - paid subscription (the number of the service plans available for subscription can be configured for each provider separately);
 -  standard procedure to confirm user subscription.

The system includes the following classes:

 - provider
 - user
 - user type
 - service
 - service_plan

![Class Diagram for the System](https://github.com/AnnaM0505/scalable_test/blob/main/class_diagram.png)

We support the user types as follows:

 - **guest**: newly registered users;
 - **basic**: users who completed the KYC procedure;
 - **advanced**: user who purchased one of the service plans available at the user's provider;
 - **company** user who purchased a corporate service plan.

The system provides time limits for a user session and the limit on the number of operations. These restrictions apply to **guest** and **basic** users only. 
| User type |Session timeout (min)  | Operation limit per day | Operation limit per week
|--|--|--|--|
| guest	 | 20| 5 | 20 |
| basic| 20| 20	| 50|

The system provides the following flows for a user:

 - Signing up
 - Becoming *idle* after reaching the session timeout/operation limit
 - Performing **Know your customer** procedure 
 - Purchasing an advanced service plan
 - Purchasing a company service plan

See the state diagram below: 

![State_Diagram_User](https://github.com/AnnaM0505/scalable_test/blob/main/user_state_diagram.png)
