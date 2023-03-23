# DaaS

**How to get started** - Well unfortunatly a lot of it isn't connected up - and I will also need to sanatize the data too before releasing the files.

Once thats done and there is a production release, I will upload the files here and provide a tutorial video on setting it up from scratch. 

# What is this?

### A free an opensource project for managing and allowing user to easily deploy containers by dynamically creating NPM endpoint URL

### Tools used in this Project:

NodeRED - What i call the DaaS translation layer - this is what binds NPM

*   Directus / MariaDB - The robust back end - and now with NodeRED alowing for schema backup /restores - this is what will be used when the Schema will be updated 
*   Appsmith - The front facing web UI for interacting and managing your containers/stacks 
*   Portainer - This is what will be used for actual deployment - but all its information will come from Directus
*   Nginx Proxy Manager - The proxy manager everyone knows and loves. I won't use traefik -  too many damn labels - but this may change in the future. as this can be managed by Directus
*   NTFY / UptimeKuma - This is mainly for Administrators to keep an eye on if endpoint / IPs go down unexpectedly.

### Features

*   Deployment restriction based off enrolment group
*   Image variability - sometimes there are environment setting for the same image and so these variation need to be accessable - Look at NPM, this can be deployed with a MariaDB or mySQL - and you can't use both! But now you can!
*   Beautiful UI for managing your account, Stacks and Containers.
*   Using DockerNursary to put containers to sleep when they aren't in use
*   Allow and limit stack deployments based off node restriction - I am running my Portainer with Edge Agents - so it makes sense to deploy heavy application on my HP Server - and have lighter application deployed on other servers.
*   VM creation and managment - This is waaaayy down the line - but definitly will be cool and convienient for users to create and spin up their own VM!
*   Create slugs for controlling your endpoints eg.  https://Gitea.\[slug/username\].domain.com
*   Create container templates that will beased off working stacks - however its not secure as its generic - its an easy way to test and just deploy something 
*   For containers that require other containers eg a container that requires a database and related Environment data  - I wil lbe looking a tcreating something that allows for linking to other Containers and dynamically updating the relationships environments between them.

### Future Features

*   Add Authelia for containers that dont have a login
*   Container Intergration with Authentik for group management  
*   Allow for users to point their own IP or Domain to a new Instance of NPM that they can run - good for people who can't afford host their own but can at least buy a domain.  
*   Allow for users to create their own database settings - as its a bit of a pain to keep having to type in all the details like hostname, port, database etc, there will be a feature to generate and autofill this for you.
*   Storage Limitations - Limit by User/ Group or container
*   Stack YML upload to Directus - have the ability to take a working stack and upload it to Directus so it can be used as a deployable template

### Currently working

*   User creation and login to Appsmith
*   At the moment I'm having to focus a lot of my time on the Directus Scheme - as this is the hardest thing to change once a collection has been created - so this needs the upmost focus - so alot of it about creating the tools required, then piecing it all together.
*   I have been working on all the pieces that will be needed to put it all together - as there are so many working parts and components - this will take time.

### To-do

Too damn much - Its only me working on this project!

*   Design a database schema thats not too time consuming to manage , while being flexable to use in as it needs to cover many deployment scenarios.
*   Create a UI using Appsmith that doesnt make you have to click on a million things for one thing to happen. - it should be a one-stop-shop.
*   Then link everything together to ensure updates and API are working correctly - I'm doing my best to createa  modular API Schema structure  in NodeRED where if something drastic changes in Directus - Updating NodeRED and Appsmith should be a fairly easy process - after all, its just data!
*   Eventually adding the awesome features this project needs - So i'm trying not to 'feature creep' on this project - I just need to get it working first!

# Images

Images are a WIP and more of a visual representation what the end user will see.

![](https://user-images.githubusercontent.com/35937684/227159651-3b774dce-60d5-45a1-83a8-975c788eec45.png)

![](https://user-images.githubusercontent.com/35937684/227159979-d668ae74-1b05-42ec-a0f6-b82582165d7a.png)

![](https://user-images.githubusercontent.com/35937684/227160485-976fdce2-3c8e-4668-a4a1-65ad75a0132c.png)

![](https://user-images.githubusercontent.com/35937684/227172999-3e474d9f-c8a1-4dc4-beb6-3634e9229f93.png)
