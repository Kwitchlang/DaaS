- ### Directus Schema
-
-
-
- OLD information
	- ## Directus
	  collapsed:: true
		- ### Image Template
			- Image ID
				- *List of the Container image url*
			- List of Image Paths
			- Image Architecture
				- *X86, ARMv7 etc*
				- *An API will be used to get this Information from Dockerhub when the image gets pulled and will be determined what server it can be deployed to*
			- Image Dependencies
				- *Useful if some container require another container to operate with : eg MariaDB*
			- Image Ports
				- *List internal ports of the image*
		- ### Container Template
			- Image Template
			- Container Hostname
			- Container Restart Policy
			- Repository
			  collapsed:: true
				- *Used as I will be caching image pulls with JFrog to save on pulls*
			- Append Service Name to Container
			  collapsed:: true
				- *This will treat Container Hostname only as the hostname and not Container_Name, keep TRUE to enable the container name to  be generate off the service - enables for scalability when there are multiple containers called the same*
				  * True: service-containerhostname-1
				  * false: container
			- Commands
			- List of Container Environments
			- Assigned Host Ports
			  collapsed:: true
				- *Assigns a list of ports from the selected image  to be available to host machine - as NPM may not be hosted on the node that the container is deployed to, it will need to be exposed*
			- Assigned Volumes
			  collapsed:: true
				- *This will be the Volume assigned to that specific Image Templates' Image Paths *
			- Network Mode
			  collapsed:: true
				- *Selects Bridge or default, more list of options of network modes will be added here - possibly for advanced user*
			- Enable Docker Nursary
			  collapsed:: true
				- *Enable the container to sleep - however this may be put in either Service Table or assigned as a policy depending on the users subscription model or Account Type*
		- ### List of Internal ports
			- Port Number
				- * What internal port is used, eg: 80, 443, 3306 will be associated with an image Any that used in the Containers' Assigned Host ports will be treated as 'exposed: (docker yaml) and not 'ports:' and will only be available to the Stacks' Containers *
			- Schema
			  collapsed:: true
				- HTTP / HTTPS
					- *This is used for NGINX Reverse Proxy Manager to determine how it needs to respond to the port, eg any external port can be anything, its what the internal ports behaves. *
			- Require Websocket
			  collapsed:: true
				- * Used for NPM - as some Containers require it to be enabled *
			- Protocol
			  collapsed:: true
				- * Some images require special requirements, like [[RustDesk]] *
				- Default - None, normal behaver
				- TCP
				- UDP
				- TCP / UDP
			- Port Description
			  collapsed:: true
				- *As this is on a per Image basis - (even though many images can have the same internal Port number, there are a lot of ports and each ports will associated with different images ) *
			- Assigned Image
		- ### Service /  Stack
		  collapsed:: true
		  *Used as an overview of deployed stacks*
			- Service Name
			- List of Assigned Containers
			- Owner
			- Deployment Node IP Address
				- *Using portainer API, what Server is this stack deployed to:*
				  *eg: 192.168.1.X | EdgeNode ID *
			- List of Endpoints:
				- *example.user.kwitchlang.com | LocaIpAddress:port | [NPM | Dockersleep]  *
				- *gitea.visc.kwitchlang.com | 192.168.1.1:6589 | NPM, DockerSleep*
				-
		- ### Policy Options
			- User Policy
				- Deployments:
				  collapsed:: true
					- User Max Deployed Stacks
					- User Max Containers allowed in Stack
					- User Max endpoints ( Nginx proxy manager URLs) per stack
					- Allow NPM Domain Access
						- * useful if say they have a Palatium Subscription, they may want to manage their own domains such as policy / user access *
					- Put container to sleep by default: yes
				- Volumes:
					- Allow Volume Backup
					- Volume Size Limit
			- Resource Policy
				- Max RAM Allocated
				- CPU Pinning
				- CPU Limit
			- SSO and other Platinum Services:
				- Authentik
				- Authelia 2FA Security