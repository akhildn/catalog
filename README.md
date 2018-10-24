# Udacity Catalog Project

Objective: Develop an application that provides a list of items within a varity of categories as well as provide a user registration and authentication system. Registered users will have ability to post, edit and delete their own items.  

For this project I have used the instructor project where categories where the restaurants. Registration and authentication is done through OAuth provided by google. On user is assigned an Id and gets registerted when they are loging in for the first time.  

## Environment:  
- Python (Flask)
- OAuth Authentication (google)
- SQLAlchemy (SQLite) 
- Bootstrap 4.0 
- Javascript
- Ajax
- Jinja2
- RESTful API

## Database

ORM: SQLAlchemy

The file `database_setup.py` is used for creating the database, you can find field names, datatypes for fileds in there. The created database is with name `restaurantmenuwithusers.db`.  

run the following command to set up the database:  
`python database_setup.py`

1. User: this table contains information of registered users. Stores information such as id, name, email and picture.  
	
	 |Column name| Description                       | Datatype and Contraints| 
	 |-----------|-----------------------------------|------------------------|
	 | id        | user id                           | integer, primary key   |
	 | name      | name of the user                  | varchar	              | 
	 | email     | email address of registerted user | varchar 				  |
	 | picture   | stores url for profile picture    | varchar                |


2. Restaurant: this table contains information of the restaurant created by the user. Stores information such as id, name, user_id.  
  
    |Column name| Description                                | Datatype and Contraints|
	|-----------|--------------------------------------------|------------------------|	 
	| id        | restaurant id                              | integer, primary key   |	
	| name      | restaurant name                            | varchar                |
	| cuisine   | restaurant cuisine type                    | varchar                |
	| address   | restaurant address                         | varchar                |
    | user_id   | user id of user who created the restaurant | integer, foreign key references user(id) |  

3. MenuItem: this tabe contains information of the items avialable in the restaurant. Stores information such as id, name, description, course, price, restaurant_id, user_id.
	
	|Column name    | Description                                | Datatype and Contraints|
	|---------------|--------------------------------------------|------------------------|	 
	| id            | item id                                    | integer, primary key   |	
	| name          | item name                                  | varchar                |
	| description   | description for the item                   | varchar                |
    | course        | name for course it belongs to              | varchar                |
	| price         | price of the item                          | varhcar                |
	| restaurant_id | restaurant id of restaurant item belongs to| integer, foreign key references restaurant(id) |
	| user_id       | user id of user who created the item       | integer, foreign key references user(id) | 	
	
## Requirements

You can run this project using Vagrant if you do not have unix based environment already set up, 
if you do you just need the e requirements which are stated below.

	###What do you need to run this project:
		1. Python : v3
		2. SQLAlchemy
		3. Flask
		4. Google OAuth credentials

	### How to set up Vagrant
		1. You can view about vagrant here : https://www.vagrantup.com/intro/index.html
		2. Download and install vagrant. (Download: https://www.vagrantup.com/downloads.html) 
		3. You would also need `Virtual Box` for the set up. (Download: https://www.virtualbox.org/wiki/Downloads)
		4. Set up the VM configuration. (You can find more info Vagrant docs). You can skip that part if you are using are files in my folder.
		5. Go to the folder which has Vagrant file, and run `vagrant up` in the shell
		6. Then type `vagrant ssh` 
		

## Setting up Google Oauth

Go through the Following links to set up Google Oauth:  
https://developers.google.com/identity/protocols/OAuth2
https://www.youtube.com/watch?v=8aGoty0VXgw

Once you have set up the OAuth, i.e. once you have client id and secret creditals json file. Place them in the code.   
1. Secret credentails json file goes in the root folder for the project with the same `client_secrets.json` 
2. Replace your client id in `/templates/guest/login.html` at line 13 where you have attribute `data-clientid`


## How to run:
- navigate to catalog folder (project folder)
- run the command `python main.py`




	


