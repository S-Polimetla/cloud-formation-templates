# IAM Cross Account Access
Consider two different teams working together. One of them is working with a Dev Account and the other is working with a Prod Account

It is often the case that the users of a account need access to the other account for certain tasks. 

The templates [dev-account-roles.yaml](dev-account-roles.yaml) and [prod-account-roles.yaml](prod-account-roles.yaml) are to be created in their respective accounts.

This cross account access enables users of respective accounts to switch to the other account without having to use additional credentials. 

All users of Admin Group in the Prod Account can assume Admin Role in the Dev Account

All users of the Dev Account including Admins can only assume Developer Role in the Prod Account
