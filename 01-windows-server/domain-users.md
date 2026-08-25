# Creating and Organizing Domain Users 

## Intro 
Now that we have our OUs and security groups created, it is time to start creating and organizing domain users within them.

## Purpose
The reason we create unique domain user accounts per individual and organize them with OUs and security groups:
- Having separate domain user accounts allows us to centrally manage and log the activity of each account
- Allows us to create an organizational structure within our Active Directory to simplify and implement policies and rules
- Helps us implement access control rules per user or role to successfully implement least privilege

In other words, the creation and organization of domain users allows us to centrally manage them from our domain controller, helping to ensure efficiency and security (if implemented correctly).

## Implementation + Results

Please note that since the last section (ous-&-groups) went into depth with explanations, this section will mostly just be concise implementations and results

### Step 1 - Create Domain Users

As shown before, we have created a handful of OUs under the `User Accounts` OU to organize all of our users. We simply navigate to our `Active Directory Users and Computers`, go within the appropriate OU, and create a new user.

*Here, we create Omar, a Finance Associate:*

![Create User](../screenshots/01-windows-server-ss/create-users.png)

![Create User Pt 2](../screenshots/01-windows-server-ss/create-users-pt2.png)

![Create User Pt 3](../screenshots/01-windows-server-ss/create-users-pt3.png)

![Create User Pt 4](../screenshots/01-windows-server-ss/create-users-pt4.png)

![Create User Pt 5](../screenshots/01-windows-server-ss/create-users-pt5.png)

![Create User Pt 6](../screenshots/01-windows-server-ss/create-users-pt6.png)


### Step 2 - Move Them to Their Dedicated OU
Now that we finally have these two core tasks completed, we can promote our server to domain controller. To do this, we first must install the Active Directory Domain Services (AD DS) role. We navigate our Server Manager, and select **Add Roles and Features**. From there we choose **Role-based or feature-based installation** as our installation type. Then, we select our server from our server pool as shown below: 

![Server Pool Selection](../screenshots/01-windows-server-ss/server_pool_selection.png)

We then install both the AD DS and DNS server roles. The remaining settings can be left at their defaults.

![Server Roles](../screenshots/01-windows-server-ss/server_roles.png)

Finally, we can promote our server to domain controller.

![DC Promotion](../screenshots/01-windows-server-ss/domain_controller_promo.png)

We are then prompted with the deployment configuration. Since we are building this primary domain controller from scratch, we select **Add a new forest**. For the root domain name, to keep it simple, I chose `home.lab`. We are then prompted to choose a Directory Services Restore Mode (DSRM) password, which we can use if we ever need to boot the server into recovery mode. A secure password was chosen accordingly for this step. If all prerequisites are met, the installation should occur successfully. We can check that the domain has been created successfully on our DNS Manager. 

![Domain Check](../screenshots/01-windows-server-ss/domain_check.png)

We can also run a health check using the command **dcdiag** on the Command Prompt to ensure everything is working. 

![dcdiag](../screenshots/01-windows-server-ss/dcdiag_check.png)

### Step 3 - Move Them to the Correct Security Group(s)

## Conclusion

And that brings us to the end of this section. 

As of now, our server:
- Has had the AD DS and DNS server roles installed
- Has been promoted to a domain controller
- Has created the `home.lab` domain

Next, we tackle our Windows Client VM!
