# Role based access control

## Why is access control important?
    Access control allows us to easily allow different functionality for different end users. There are many applications for this including encorporating a paywall for premium content, or for a publication that wants to allow anyone to submit articles, but only some individuals can moderate or approve those submissions etc.
## Describe an application that would need access control.
sometimes organizations like the Seattle Times will allow a certain number of views for free, but then after those views have been reached only want to allow people who have paid/(can log in) to be allowed to read the content behind their "paywall". 
## What is a role used for?
Roles allow the developer to assign different abilities/permissions to each role. For instance, editor, admin, writer, and then one for a regular everyday user who has no special permissions. 
## Why is role based access control more scalable than discretionary or mandatory access control?
because it is built with this functionality in mind the building blocks are already there. It is quite simple to adjust the permissions of users when it's built in to the user model. 
## Document the following Vocabulary Terms

## Authorization
Authorization is the function of specifying access rights/privileges to resources, which is related to information security and computer security in general and to access control in particular.[1] More formally, "to authorize" is to define an access policy. For example, human resources staff are normally authorized to access employee records and this policy is usually formalized as access control rules in a computer system. During operation, the system uses the access control rules to decide whether access requests from (authenticated) consumers shall be approved (granted) or disapproved (rejected).[2] Resources include individual files or an item's data, computer programs, computer devices and functionality provided by computer applications. Examples of consumers are computer users, computer Software and other Hardware on the computer.
resource: https://en.wikipedia.org/wiki/Authorization

## Role Based Access Control
In computer systems security, role-based access control (RBAC)[1][2] or role-based security[3] is an approach to restricting system access to authorized users. It is used by the majority of enterprises with more than 500 employees,[4] and can implement mandatory access control (MAC) or discretionary access control (DAC).

Role-based access control (RBAC) is a policy-neutral access-control mechanism defined around roles and privileges. The components of RBAC such as role-permissions, user-role and role-role relationships make it simple to perform user assignments. A study by NIST has demonstrated that RBAC addresses many needs of commercial and government organizations [5]. RBAC can be used to facilitate administration of security in large organizations with hundreds of users and thousands of permissions. Although RBAC is different from MAC and DAC access control frameworks, it can enforce these policies without any complication.
resource: https://en.wikipedia.org/wiki/Role-based_access_control
## Capabilities

capabilities in this context, refers to the particular abilities that are available for the individual within their particular "role". The capabilities of a moderator will be far greater than those of a everyday user of a chat room. 