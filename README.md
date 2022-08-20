# ABOUT THE PROJECT:

The YaMDb project collects user reviews of works. The works are divided into categories: "Books", "Films", "Music". The list of categories can be expanded by the administrator (for example, you can add the category "Fine Art" or "Jewelry").
The works themselves are not stored in YaMDb, you can't watch a movie or listen to music here.
Grateful or outraged users leave text reviews for the works and give the work a rating in the range from one to ten. The user can leave only one review for one work.


## How to launch a project:

Clone the repository and go to it on the command line:

```
git clone https://github.com/sakson-is-man/api_yamdb.git
```

```
cd api_yamdb
```

Create and activate a virtual environment:

```
python -m venv venv
```

```
source venv/Scripts/Activate
```

```
python -m pip install --upgrade pip
```

Install dependencies from a file requirements.txt:

```
pip install -r requirements.txt
```

Perform migrations:

```
python manage.py migrate
```

Launch a project:

```
python manage.py runserver
```

## authorization

###Registering a new user

Send a POST request to /api/v1/auth/signup/ specifying username and email in the request.

```
{
  "email": "string",
  "username": "string"
}
```
**Attention!!! It is forbidden to use the name 'me' as a username.**

A confirmation code will be sent in response to the email.

###Getting a JWT token

Send a POST request to /api/v1/auth/token/ specifying the username and confirmation code received by email in the request

```
{
  "username": "string",
  "confirmation_code": "string"
}
```
A token will be sent in response to the email.

```
{
  "token": "string"
}
```


# Example of using the API:

##Getting a list of all works

Send a GET request to /api/v1/titles/.
In response, you will receive a json with a list of all the works:

```
[
  {
    "count": 0,
    "next": "string",
    "previous": "string",
    "results": [
      {
        "id": 0,
        "name": "string",
        "year": 0,
        "rating": 0,
        "description": "string",
        "genre": [
          {
            "name": "string",
            "slug": "string"
          }
        ],
        "category": {
          "name": "string",
          "slug": "string"
        }
      }
    ]
  }
]
```

##Adding a work

Send a POST request to /api/v1/titles/ with a json string:

```
{
  "name": "string",
  "year": 0,
  "description": "string",
  "genre": [
    "string"
  ],
  "category": "string"
}
```
<<<<<<< HEAD
>**Нельзя добавлять произведения, которые еще не вышли (год выпуска не может быть больше текущего).**
>**При добавлении нового произведения требуется указать уже существующие категорию и жанр.**

=======
>**It is not allowed to add works that have not yet been released (the year of release cannot be greater than the current one).**
>**When adding a new work, you need to specify the already existing category and genre.**
>>>>>>> fe4fad4d8488f5526878f58e5d9020ff2ad76a74
