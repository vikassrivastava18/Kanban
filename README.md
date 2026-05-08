# Kanban-vue-flask
A multiuser Kanban application for managing daily tasks.

## Summary
- A user needs to register for the application with a username, email and password. Authentication is done with JWT. Once registered, they can create lists and cards for daily tasks.
  
- A card has the information about the deadline and the completion time. Comparing the completion time and the deadline, one can tell if the card was not finished in time, is pending, or delayed.

- A card can be moved from one list to another using drag and drop.
  
- The card can be edited or deleted by the user.

- Daily/monthly reminder - User gets the reminder for the tasks not completed before the set deadline, through Google-chat webhook.

- Export - the list information can be exported by the user in csv format.

## Description
A multiuser Kanban application for managing daily tasks.

# Tools
- Flask - For creating the backend
- Sqlite - For saving the data
- Vue - For creating the frontend
- Flask-Sqlalchemy - For interacting with the database
- Flask-jwt - For authentication (token based)
- Bootstrap - For the layout and styling
- Celery, Redis - For the schedulers


## DB Schema Design

+----------------------+        1          many        +----------------------+        1          many        +----------------------+
|        User          |------------------------------>|        List          |------------------------------>|        Card          |
+----------------------+                               +----------------------+                               +----------------------+
| PK userid : integer  |                               | PK list_id : integer |                               | PK card_id : integer |
| username : string    |                               | name : string        |                               | FK list : integer    |
| email : string       |                               | FK user : integer    |                               |   → List.list_id     |
| password : string    |                               |   → User.userid      |                               +----------------------+
| active : boolean     |                               +----------------------+
+----------------------+



