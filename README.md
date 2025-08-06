

# Laravel Blog API application

### This is  a Laravel 12 Project make sure you have a php version for that. [Laravel documentation](https://laravel.com/docs/8.x/releases)

# Description

### This is a simple blog API application built with Laravel for a Nuxt.js frontend application allows users to create, read, update, and delete blog posts. The backend is built using Laravel, a popular PHP framework, and follows Laravel's coding standards based on the PHP Standards Recommendations.


## Features

- User authentication with Laravel Passport
- CRUD operations for blog posts


### Steps to run this project:

1. git clone `https://github.com/paulbless/laravel-12-nuxt-api.git`

2. cd in `laravel-12-nuxt-api`

3. Run `composer install` command

4. Run `php artisan migrate` command for database

5. Run `php artisan serve` command


# Api Documentation

## PUBLIC ENDPOINTS

### 1. [User Model : create user]()

```js
POST
```

Endpoint

```js
	/register
```

Request body

```js
	{
	  "name": "string",
	  "email": "string",
     "password": "string",
	}
```

Response body

```js
	{
		user: {
		  "name": "string",
		  "email": "string",
		},
		message:"user account was created successfully !"
	}
```


### 2. [User Model : login user]()

```js
	POST
```

Endpoint

```js
	/login
```

Request body

```js
	{
	  "email": "string",
	  "password": "string"
	}
```

Response body

If user provide invalid credentials
```js
	{
		"isLogged":false,
		"message":"email or password invalid",
	}
```

If user provide valid credentials
```js
	{
		user: {
		  "name": "ben",
		  "email": "ben@gmail.com",
		},
		"isLogged":true,
		"message":"user logged",
		"token":"$2b$10$0O.pVCtZO2QgxfPKh0WNsudCHglKsoGwhJ0GXciLYzHCa73x99Gpa"
	}
```

### 3. [User Model : logout user]()

```js
	POST
```

Endpoint
```js
	/logout
```

Request body

```js
	{
		"userId": 1,
	}
```

Response body with status 200
```js
	{
	  "message":"user logged out !"
	}
```



##  SECURED ENDPOINTS : admin

### 1. [Post Model : create post]()

```js
	POST
```

Endpoint
```js
	/posts
```

Request body

```js
	{
		"title": "What is TypeScript",
		"post_content":"content...."
	}
```

Response body with status 200
```js
	{
	  "message":"Post created successfully !"
	}
```


### 2. [Post Model : update post]()

```js
	PUT
```

Endpoint
```js
	/posts/:id
```

Request body

```js
	{
		"title": "What is TypeScript",
		"post_content":"content...."
	}
```

Response body with status 200
```js
	{
	  "message":"Post created !"
	}
```


### 3. [Post Model : delete post]()

```js
	DELETE
```

Endpoint
```js
	/posts/:id
```

Request body

```js

```

Response body with status 200
```js
	{
	  "message":"Post deleted !"
	}
```



### 4. [Post Model : upload Image post]()

```js
	POST
```

Endpoint
```js
	/posts/upload-image
```

Request body

```js
	{
		"postId": "number",
		"image":"binary"
	}
```

Response body with status 200
```js
	{
	  "message":"Post image uploaded !"
	}
```




##  PUBLIC API : WEBSITES

### 4. [Post Model :get post]()

This endpoints is used to display details of a single post

```js
	GET
```

Endpoint
```js
	/posts/:slug
```

Response body with status 200
```js
[
	{
	"id": 8,
	"title": "What is TypeScript",
	"post_content": "<p></p>",
	"image": "http://127.0.0.1:8000/storage/images/1711706289.jpg",
	"slug": "what-is-typescript-xGckmQ1711806376",
	"created_at": "2024-03-11T17:44:03.000000Z",
	"updated_at": "2024-03-30T13:46:16.000000Z"
	}
]
```



### 5. [Post Model :getPosts]()

Return a list of posts 

```js
	GET
```

Endpoint
```js
	/posts?query=
```

Response body with status 200
```js
{
	"data": [
		{
		"id": 3,
		"title": "What is Golang ?",
		"post_content": "<p>",
		"image": "http://127.0.0.1:8000/storage/images/1711706163.jpg",
		"slug": "what-is-golang-lZg1Ap1711810344",
		"created_at": "2024-03-10 14:32:29",
		"updated_at": "2024-03-30 14:52:24"
		}
	]
}

```



### 6. Return number of created posts



```js
	GET
```

Endpoint
```js
	/count/posts
```

Response body with status 200
```js
{
	"data": 5
}

```


### 7. Check if user is logged in[return true or false]



```js
	GET
```

Endpoint
```js
	/check/user/loggedin
```

Response body with status 200
```js
{
	"success": true
}

```


### 8. return a list of posts



```js
	GET
```

Endpoint
```js
	/client/posts
```

Response body with status 200
```js
[
	
	{
		"id": 5,
		"title": "What is TypeScript",
		"post_content": "",
		"image": "http://127.0.0.1:8000/storage/images/1715743244.jpg",
		"slug": "what-is-typescript-8yXHkQ1715743297",
		"created_at": "2024-05-15 03:20:05",
		"updated_at": "2024-05-15 03:21:37"
	},

]

```



### 8. Check if user is authenticated

```js
	POST
```

Endpoint
```js
	/user-logged-in
```


Response body with status 200
```js
{
	success:true
}

```
