# Creating and Implementing GPOs

## Intro 
Now that we have our domain users created organized within our OUs, we can now create and implement our Group Policy Objects (GPOs). In this section we will implement 4 GPOs. The first will be a domain-wide password policy. The second will be a workstation policy that provides device-level security. And the last two will be department-specific policies for the IT and Finance departments.

## Purpose
The reason we implement GPOs within a domain are plentiful, here are the reasons relevant to this lab:
- GPOs allow us to establish domain-wide policies that impact all domain users, a very important example being **Password Policies**, which help to enforce secure password requirements
- They can also be more granular, allowing us to create security and configuration policies for overarching OUs such as `Workstations` or `User Accounts`
- Lastly, they can help us implement policies specific to a department such as our `IT` OU, without affecting users in other department OUs

In other words, GPOs let us centrally enforce security and configuration policies across the domain while also allowing specific policies to be applied to individual OUs. This helps maintain consistent security standards while adapting policies to the needs of different users and devices.

## Implementation + Results

### GPO #1 - Domain-Wide Password Policies


![Create User](../screenshots/01-windows-server-ss/create-users.png)


### GPO #2 - Workstation Security Policy


![Create User](../screenshots/01-windows-server-ss/create-users.png)


### GPO #3 - IT User Security Policy


![Create User](../screenshots/01-windows-server-ss/create-users.png)


### GPO #4 - Finance User Security Policy


![Create User](../screenshots/01-windows-server-ss/create-users.png)


## Conclusion

That brings us to the end of this section. 

As of now have implented:
- ...

Next, we move on to file sharing and access controls.
