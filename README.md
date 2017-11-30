Dynamic 3scale Developer Portal signup templates
================================================
There are 4 custom signup flows included in the [parent homepage](https://gist.github.com/kevprice83/5c673c074fde190771e06967bf8ae232#file-index-html-liquid). These flows are included into the homepage using Liquid tags such as `{% include 'partial name' %}` because the flows are separated out into individual partials. The partials can be included in your 3scale portal individually or all together depending on which flows you want to enable in your portal and for ease of switching between flows as and when needed.

---

How does the 3scale signup work?
--------------------------------
### The Basics
A developer can sign up to subscribe to an API service in various ways and how they do that is determined by the configuration of all the settings on the 3scale Admin Portal. Although this is flexible and varying in terms of the process and mechanics working in the background, the end user will not see a great deal of difference from their persepctive and this is key to delivering a good user experience.

Typically the developer would be able to discover any API service and the differing plans (contracts) as a public user on the homepage of any Developer Portal, when choosing the service and plan to subscribe to, the necessary parameters to create the contract between the Account and the API service will be passed to the signup form. There will be an Application created in the background as part of the signup process as this is the object that contains the API keys for consuming the contracted services.

### Objects created during signup
- Account
- User
- Application
- Key(s)

The Account can have many Users but will only have 1 upon initial creation. If the Account has subscribed to multiple Services in the signup then it will be associated to those Services via what's known as a Service subscription and for each Service subscribed an Application will be created along with a set of Keys. Although it is important to understand the 3scale data object model and the relationship each object has with one another we won't go into too much detail on that here.

### Subscriptions
There are 2 different subscriptions made when the signup is completed. The user commonly only really sees and cares about one of these though. The most important subscription is the Application Subscription and the less important of the two is the Service Subscription.

##### Application Subscription
The Application object has 1:1 relationship to a Service via an Application Plan in 3scale. This is the contract that determines the level of access, rate limits & pricing tier (if it's a monetized API) to consume a single Service.

##### Service Subscription
The Account object can be subscribed to many Services in 3scale and is able to access those Services via the Service Plan -- we use this only to manage the APIs the Account has access to -- as an admin user you will see these subscriptions in the Admin portal as a list of Service Subscriptions.

The Signup Flows
---------
### Single Application Flow
This is the simplest signup flow that only allows a signup to a single Service and Application Plan upon account creation. No features need to be enabled in the 3scale Developer portal to use this flow. Just include the [single app partial](https://gist.github.com/kevprice83/5c673c074fde190771e06967bf8ae232#file-_single_app_signup_form-html-liquid) from your [homepage](https://gist.github.com/kevprice83/5c673c074fde190771e06967bf8ae232#file-index-html-liquid) with: `{% include '<PARTIAL_NAME>' %}`.

### Multiple Application flow
This is a fairly simple signup flow that allows any public users to signup directly to multiple services and the associated Application Plans in just one sign up form. The user does not need an account prior to the signup as we want the Services to be publicly available. The Multiple Applications feature -- *Developer portal > Feature visibility* -- needs to be enabled on the Developer portal to use this flow. Use the [multiple apps partial](https://gist.github.com/kevprice83/5c673c074fde190771e06967bf8ae232#file-_mulitple_app_signup_form-html-liquid) and call it from the 
[homepage](https://gist.github.com/kevprice83/5c673c074fde190771e06967bf8ae232#file-index-html-liquid) as so: `{% include '<PARTIAL_NAME>' %}`.

### Flow 3
Group Memberships flow. This requires a user to have signed up to create an account previously. None of the services or plans are exposed publicly. The account will be approved by an admin of the API provider team and subsequently assigned the appropriate Group Membership. This will in turn expose the relevant APIs and their plans on the homepage for subscription. To enable this flow a series of steps must be followed. `TODO`: list settings in admin portal required.

### Flow 4 
Custom Fields flow. To use this flow a custom field on the Account object will need to be defined with some options. These values will then be filtered using some Liquid logic to render the allowed services and plans for the logged in user. Again an account will need to be created by the user before they can subscribe to any services. `TODO`: list settings in admin portal required.