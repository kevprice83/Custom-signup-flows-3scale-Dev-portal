### Dynamic 3scale Developer Portal signup templates

There are a few custom signup flows included in the single parent homepage here. These templates and partials can be included in your 3scale portal individually or altogether depending on which flows you want to enable in your portal.

#### Flow 1

Multiple apps flow. This is a simple signup flow that allows any public users to signup directly to multiple services and the associated application plans. The user does not need an account prior to signup. The Mutliple Applications feature needs to be enabled on the Developer portal to use this flow.

### Flow 2

Single app flow. This is the simplest signup flow that only allows a signup to a single service and application plan upon account creation. No features need to be enabled in the 3scale Developer portal to use this flow.

### Flow 3

Group Memberships flow. This requires a user to have signed up to create an account previously. None of the services or plans are exposed publicly. The account will be approved by an admin of the API provider team and subsequently assigned the appropriate Group Membership. This will in turn expose the relevant APIs and their plans on the homepage for subscription. To enable this flow a series of steps must be followed. `TODO`: list settings in admin portal required.

### Flow 4 

Custom Fields flow. To use this flow a custom field on the Account object will need to be defined with some options. These values will then be filtered using some Liquid logic to render the allowed services and plans for the logged in user. Again an account will need to be created by the user before they can subscribe to any services. `TODO`: list settings in admin portal required.