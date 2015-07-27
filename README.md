# **Zero Issue Game API**
* Ruby version
__ruby 2.1.5p273__

Zero Issue is a fun app where the user can take an image of a person on their smart phone, and transform the way they look through a library of comic book themed assets.  The user can then go online and view all of their photos to create their own comic book strip.  
We built this app in 48 hours for our Hack-A-Thon, and took 1st Place for having the most polished result in such a short period of time.  

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
* [Show Comic](#show-comic)
`GET'/comic/title'`
* [Create Comic](#create-comic)
`POST '/comics/create'`
* [Get All Of A Users Comics](#get-all-of-a-users-comics)
`GET 'comics/user'`

### **Photos**
* [Create Photo](#create-photo)
`POST 'photos/create'`
* [Get A Users Photos](#get-a-users-photos)
`GET 'photos/user'`
* [Get A Users Photo](#get-a-users-photo)
`GET 'photo/:id'`
* [Get All Photos From All Users](#get-all-users-photos)
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
    "comic_url": "www.madeupurl.com",
    "title": "zero issue",
    "user_id": 1,
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
  * comic_url
  * title

Response:
  Status Code: 201 if successful, 422 if unsuccessful

Example success:  
```json
{
  "id": 4,
  "comic_info": {
    "comic_url": "www.madeupurl.com",
    "title": "First Issue",
    "user_id": 1,
    "created_at": "2015-06-28T11:36:09.556Z",
    "updated_at": "2015-06-28T11:36:09.556Z"
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



### **Get All Of A User's Comics**

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
    "id": 4,
    "comic_info": {
      "comic_url": "www.madeupurl.com",
      "title": "First Issue",
      "user_id": 1,
      "created_at": "2015-06-28T11:36:09.556Z",
      "updated_at": "2015-06-28T11:36:09.556Z"
    },
    "creator": {
      "username": "jsmith1234",
      "email": "jsmith@tiy.com"
    }
  },
  {
    "id": 3,
    "comic_info": {
      "comic_url": "www.madeupurl.com",
      "title": "Last Issue",
      "user_id": 1,
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
      "comic_url": "www.madeupurl.com",
      "title": "Second Issue",
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
      "title": "Third Issue",
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
{ "message":"Access Token Not Found" }
```



### **Create Photo**

`POST 'photos/create'`

Params:
  * image_url:string
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
  * Allows user to select a single photo from a user by photo id

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
