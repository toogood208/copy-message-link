# Zuri Chat DM (Copy Message Link API)

Connect With Us: `developer@zuri.chat`
Zuri Chat is an open source slack clone. However, it offers a lot more functionality via a plugin system where each room can be provided by a different plugin provider.
​
## **Authentication**
this API does not require any authentication for use, 

## **Errors**
When an error occurs, you will receive an error object. Most of these error objects contain an error code and an error description so that your applications can more efficiently identify the problem.
​
If you get a 4xx response code, then you can assume that there is a bad request from your end. In this case, 
check the [Standard Error Responses](#standard-error-responses) for more context.
​
5xx errors suggest a problem on server's end.
​
​
​
## API methods:
- GET

## End Points:
base url: https://dm.zuri.chat/docs/v1
### /copymessagelink/{message_id}
- **Endpoint**: copymessagelink/{message_id}
- **Method**: GET
- **Description**: This is used to retrieve a single message. It takes a message_id as query params.
If message_id is provided, it returns a dictionary with information about the message,
or a 204 status code if there is no message with the same message id.
I will use the message information returned to generate a link which contains a room_id and a message_id
#### parameters: 
| Name | Data type |
|--------|-------------|
| message_id (required)| string |


#### how to copy a message link
- use the endpoint **https://dm.zuri.chat/api/v1/copymessagelink/**
- input the message_id after the stroke  **https://dm.zuri.chat/api/v1/copymessagelink/message_id**
- it will create a room and return the **mesaage_id**,**room_id** and **the message_link**, the message link contains the messages
***please note the createroom is a get method***


##### Example: 

```sh
https://dm.zuri.chat/api/v1/copymessagelink/61480c0de4b2aebf8ec8c866

```
##### response:

```json
code:201
 { 
    "room_id": "6146d126845b436ea04d102e",
    "message_id": "61480c0de4b2aebf8ec8c866",
    "link": "https://dm.zuri.chat/getmessage/6146d126845b436ea04d102e/61480c0de4b2aebf8ec8c866"
 }
```
the link contains the message information
example of information in a link:
```json
link: "https://dm.zuri.chat/getmessage/6146d126845b436ea04d102e/61480c0de4b2aebf8ec8c866"

  "_id": "61480c0de4b2aebf8ec8c866",
    "created_at": "2021-09-20T04:20:28.965457Z",
    "media": [],
    "message": "Hello",
    "pinned": false,
    "reactions": [],
    "read": false,
    "room_id": "6146d126845b436ea04d102e",
    "saved_by": [],
    "sender_id": "6146ce37845b436ea04d102d",
    "threads": []
``` 

```sh
Code: 500
 Description: bad request
{
  "status": 400,
  "message": "internal server error"
}
```

