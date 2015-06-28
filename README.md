# **Zero Issue Game API**
* Ruby version
__ruby 2.1.5p273__

### **Base URL: https://evening-escarpment-7913.herokuapp.com/**


### **User**
* [Get All Users](#get-all-users)
`GET '/users'`
* [Register User](#register-user)
`POST '/users/register'`
* [Login User](#login-user)
`POST '/users/login'`

### **Comics**
* [Get All Comics](#get-all-comics)
`GET '/comics'`
* [Show Comic](#show-Comic)
`GET'/comic/title'`
* [Create Comic](#create-comic)
`POST '/comics/create'`
* [Get All Of User's Comics](#get-all-of-user's-comics)
`GET 'comics/user'`

### **Photos**
* [Create Photo](#create-photo)
`POST 'photos/create'`
* [Get A User's Photos](#get-a-user's-photos)
`GET 'photos/user'`
* [Get A User's Photo](#get-a-user's-photo)
`GET 'photo/:id'`
* [Get All Photos From All Users](#get-all-users'-photos)
`GET 'photos/users'`


### **Get All Users**

`GET '/users'`

Params:
  * none
  * Returns and array of all users


Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "user": [
    {
      "id": 1,
      "username": "jsmith1234",
      "access_token": "083a050c4b1556c5b8ca68612f2b5c9f",
      "email": "jsmith@tiy.com"
    },
    {
      "id": 2,
      "username": "BJohnson1234",
      "access_token": "c9d85bbde2fde34c1cab0e1995216043",
      "email": "BJohnson@tiy.com"
    },
    {
      "id": 3,
      "username": "TMcGraw1234",
      "access_token": "908ab2d13e18b6d436c2908f83fe9adf",
      "email": "TMcGraw@tiy.com"
    }
  ]
}```
Example failure:
```json
  {"errors": ["errors":["Email has already been taken"]]}
```


### **Register User**

`POST '/users/register'`

Params:
  * username: a string
  * email: a string
  * password: a string

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "user": {
    "id": 1,
    "username": "jsmith1234",
    "access_token": "083a050c4b1556c5b8ca68612f2b5c9f",
    "email": "jsmith@tiy.com"
  }
}
```
Example failure:
```json
  {"errors": ["errors":["Email has already been taken"]]}
```


### **Login User**

`POST '/users/login'`

Params:
  * username: a string
  * password: a string

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "user": {
    "id": 3,
    "username": "TMcGraw1234",
    "access_token": "908ab2d13e18b6d436c2908f83fe9adf",
    "email": "TMcGraw@tiy.com"
  }
}
```
Example failure:
```json
{ "message":"Invalid Login" }
```



### **Get All Comics**

`GET 'comics'`

Params:
  * none
* Returns array of comics from all users.

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
[
  {
    "id": 3,
    "comic_info": {
      "comic_url": "www.madeupurl.com",
      "title": "Last Issue",
      "user_id": 2,
      "created_at": "2015-06-28T10:37:01.485Z",
      "updated_at": "2015-06-28T10:37:01.485Z"
    },
    "creator": {
      "username": "jkrowling1234",
      "email": "jkroweling@tiy.com"
    }
  },
  {
    "id": 2,
    "comic_info": {
      "comic_url": "www.madeupurl.com",
      "title": "Zero Issue",
      "user_id": 1,
      "created_at": "2015-06-27T23:18:40.137Z",
      "updated_at": "2015-06-27T23:18:40.137Z"
    },
    "creator": {
      "username": "jsmith1234",
      "email": "jsmith@tiy.com"
    }
  },
  {
    "id": 1,
    "comic_info": {
      "comic_url": "www.madeupurl.com",
      "title": "First Issue",
      "user_id": 1,
      "created_at": "2015-06-27T23:14:48.600Z",
      "updated_at": "2015-06-27T23:14:48.600Z"
    },
    "creator": {
      "username": "jsmith1234",
      "email": "jsmith@tiy.com"
    }
  }
]
```
Example failure:
```json
  {"errors": ["errors":["Error"]]}
```

### **Show Comic**

`GET 'comic/title'`

Params:
  * id
  * Returns the selected comic.


Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "id": 1,
  "comic_info": {
    "comic_url": "www.madeupurl.com/image",
    "title": "Zero Issue",
    "created_at": "2015-06-27T23:14:48.600Z",
    "updated_at": "2015-06-27T23:14:48.600Z"
  },
  "creator": {
    "username": "jsmith1234",
    "email": "jsmith@tiy.com"
  }
}
```
Example failure:
```json
  {"errors": ["errors":["Error when loading comic"]]}
```


### **Create Comic**

POST '/comics/create'

Params:
  * none
* Returns a single post

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "id": 3,
  "comic_info": {
    "comic_url": "www.madeupurl.com/image",
    "title": "First Issue",
    "created_at": "2015-06-28T10:37:01.485Z",
    "updated_at": "2015-06-28T10:37:01.485Z"
  },
  "creator": {
    "username": "jsmith1234",
    "email": "jsmith@tiy.com"
  }
}
```
Example failure:
```json
{ "message":"Access Token Not Found" }
```



### **Get All Of User's Comics**

`GET 'comics/user'`

Params:
  * none
* Retrieves all of a user's comics.



Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
[
  {
    "id": 3,
    "comic_info": {
      "comic_url": "www.madeupurl.com/image3",
      "title": "First Issue",
      "created_at": "2015-06-28T10:37:01.485Z",
      "updated_at": "2015-06-28T10:37:01.485Z"
    },
    "creator": {
      "username": "jsmith1234",
      "email": "jsmith@tiy.com"
    }
  },
  {
    "id": 2,
    "comic_info": {
      "comic_url": "www.madeupurl.com/image2",
      "title": "Zero Issue",
      "created_at": "2015-06-27T23:18:40.137Z",
      "updated_at": "2015-06-27T23:18:40.137Z"
    },
    "creator": {
      "username": "jsmith1234",
      "email": "jsmith@tiy.com"
    }
  },
  {
    "id": 1,
    "comic_info": {
      "comic_url": "www.madeupurl.com",
      "title": "Last Issue",
      "created_at": "2015-06-27T23:14:48.600Z",
      "updated_at": "2015-06-27T23:14:48.600Z"
    },
    "creator": {
      "username": "jsmith1234",
      "email": "jsmith@tiy.com"
    }
  }
]
```
Example failure:
```json
{ "message":"Access Token Not Found" }
```



### **Create Photo**

`POST 'photos/create'`

Params:
  * none
* Removes validated users' post

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "photo_info": {
    "photo": 8,
    "image_url": "www.google.com/image",
    "comic_id": null,
    "user_id": 1
  }
}```
Example failure:
```json
{ "message":"ERROR" }
```


### **Get A User's Photos**

`GET 'photos/user'`

Params:
  * Retrieve photos by user

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
[
  {
    "photo_info": {
      "photo": 8,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 7,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 6,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 2,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  }
]
```
Example failure:
```json
{ "message":"User Does Not Have Any Photos" }
```

### **Get A User's Photo**

`GET 'photo/:id'`

Params:
  * :id
  * Allows user to select a single photo from a user by photo id.

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "photo_info": {
    "photo": 2,
    "image_url": "www.google.com/image",
    "comic_id": null,
    "user_id": 1
  }
}
```
Example failure:
```json
{ "message":"This user does not have any photos." }
```
### **Get All Photos From All Users**

`GET 'photos/users'`

Params:
  * none

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
[
  {
    "photo_info": {
      "photo": 8,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 7,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 6,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 5,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 2
    }
  },
  {
    "photo_info": {
      "photo": 4,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 2
    }
  },
  {
    "photo_info": {
      "photo": 3,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 3
    }
  },
  {
    "photo_info": {
      "photo": 2,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 1
    }
  },
  {
    "photo_info": {
      "photo": 1,
      "image_url": "www.google.com/image",
      "comic_id": null,
      "user_id": 2
    }
  }
]
```
Example failure:
```json
{ "message":"No photos exist" }
```
