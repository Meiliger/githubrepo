# Postman

Base URL: petstore.swagger.io/v2
***

*1. Add a new pet to the store*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/List%20Users%20-%20Valid.png)
</details>

```
Method: POST
EndPoint: /pet
Body:
{
  "id": 0,
  "category": {
    "id": 0,
    "name": "monkey"
  },
  "name": "Abu",
  "photoUrls": [
    "string"
  ],
  "tags": [
    {
      "id": 0,
      "name": "string"
    }
  ],
  "status": "available"
}

Response: 
{
    "id": 9223372036854604509,
    "category": {
        "id": 0,
        "name": "monkey"
    },
    "name": "Abu",
    "photoUrls": [
        "string"
    ],
    "tags": [
        {
            "id": 0,
            "name": "string"
        }
    ],
    "status": "available"
}
```

*2. Find a pet*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Single%20User%20-%20Valid.png)
</details>

```
Method: GET
EndPoint: /v2/pet/{{petId}}

Tests:
pm.test("Status code is 200", function () {
    pm.response.to.have.status(200);
});

pm.test("Body matches string", function () {
    var jsonBody = pm.response.json();
    pm.expect(jsonBody.category.name).to.include("monkey");
});

pm.test("Body matches string", function () {
    var jsonBody = pm.response.json();
    pm.expect(jsonBody.name).to.include("Abu");
});

pm.test("Response time is less than 200ms", function () {
    pm.expect(pm.response.responseTime).to.be.below(200);
});

console.log('myMessage');

Response: 
{
    "id": 9223372036854604509,
    "category": {
        "id": 0,
        "name": "monkey"
    },
    "name": "Abu",
    "photoUrls": [
        "string"
    ],
    "tags": [
        {
            "id": 0,
            "name": "string"
        }
    ],
    "status": "available"
}
```

*3. Get pet by status*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/list%20Resource%20-%20valid.png)
</details>

```
Method: GET
EndPoint: /pet/findByStatus
Request url params: 
	status: sold

<details>
  <summary>Response:</summary>
  
	12345
	
  ![Postman](
  
  [
    {
        "id": 24093935,
        "category": {
            "id": -6714225,
            "name": "do magna"
        },
        "name": "doggie",
        "photoUrls": [
            "aute",
            "velit"
        ],
        "tags": [
            {
                "id": 71561130,
                "name": "deserunt ut occaecat"
            },
            {
                "id": -1195842,
                "name": "nulla nostrud occaeca"
            }
        ],
        "status": "sold"
    },
    {
        "id": 9223372036854604228,
        "category": {
            "id": 63369977,
            "name": "enim nostrud proident eiusmod"
        },
        "name": "doggie",
        "photoUrls": [
            "magna ut",
            "exercitation ut"
        ],
        "tags": [
            {
                "id": -49719165,
                "name": "quis sint ad"
            },
            {
                "id": 12147847,
                "name": "sunt amet laboris"
            }
        ],
        "status": "sold"
    },
    {
        "id": 6479003,
        "category": {
            "id": -4830501,
            "name": "irure adipisicing e"
        },
        "name": "doggie",
        "photoUrls": [
            "sit elit",
            "commodo quis pariatur cupidatat"
        ],
        "tags": [
            {
                "id": -53025539,
                "name": "proident et reprehenderit"
            },
            {
                "id": 76820909,
                "name": "labore ullamco"
            }
        ],
        "status": "sold"
    },
    {
        "id": 9223372036854604241,
        "category": {
            "id": 13901210,
            "name": "Lorem"
        },
        "name": "doggie",
        "photoUrls": [
            "irure",
            "amet mollit"
        ],
        "tags": [
            {
                "id": 62083722,
                "name": "proident magna consequat"
            },
            {
                "id": 83179165,
                "name": "commodo sint"
            }
        ],
        "status": "sold"
    },
    {
        "id": 3708840,
        "category": {
            "id": 9855812,
            "name": "Duis in commodo"
        },
        "name": "doggie",
        "photoUrls": [
            "minim id in sit",
            "est esse culpa nisi"
        ],
        "tags": [
            {
                "id": -89808508,
                "name": "sit"
            },
            {
                "id": -5238278,
                "name": "dolor in"
            }
        ],
        "status": "sold"
    },
    {
        "id": 91507602,
        "category": {
            "id": -95494262,
            "name": "sit ea"
        },
        "name": "doggie",
        "photoUrls": [
            "deserunt",
            "id sint et"
        ],
        "tags": [
            {
                "id": -54029842,
                "name": "ullamco"
            },
            {
                "id": 13198949,
                "name": "id"
            }
        ],
        "status": "sold"
    },
    {
        "id": 9223372036854604265,
        "category": {
            "id": -52311390,
            "name": "enim tempor labore sit amet"
        },
        "name": "doggie",
        "photoUrls": [
            "magna officia aute",
            "cillum labore qui"
        ],
        "tags": [
            {
                "id": -40013794,
                "name": "in irure sit Duis"
            },
            {
                "id": -72219424,
                "name": "labore aliquip aliqua"
            }
        ],
        "status": "sold"
    },
    {
        "id": 3903023,
        "category": {
            "id": -56789506,
            "name": "cillum p"
        },
        "name": "doggie",
        "photoUrls": [
            "aliquip Excepteur",
            "commodo dolore consequat eu"
        ],
        "tags": [
            {
                "id": 60937326,
                "name": "irure in"
            },
            {
                "id": 20218536,
                "name": "sint consectetur ad voluptate"
            }
        ],
        "status": "sold"
    },
    {
        "id": 9223372036854604679,
        "category": {
            "id": 48345351,
            "name": "dolore quis"
        },
        "name": "doggie",
        "photoUrls": [
            "deseru",
            "nisi aute do incididunt"
        ],
        "tags": [
            {
                "id": 72677302,
                "name": "in incididunt dolore occaecat"
            },
            {
                "id": -38449077,
                "name": "adipisicing"
            }
        ],
        "status": "sold"
    }
]
)
</details>



```
*4. Show single <RESOURCE>*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Single%20Resource%20-%20Valid.png)
</details>

```
Method: GET
EndPoint: /api/unknown/4

Response:
{
    "data": {
        "id": 4,
        "name": "aqua sky",
        "year": 2003,
        "color": "#7BC4C4",
        "pantone_value": "14-4811"
    },
    "support": {
        "url": "https://reqres.in/#support-heading",
        "text": "To keep ReqRes free, contributions towards server costs are appreciated!"
    }
}
```

*5. Delayed response*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Delayed%20Response.png)
</details>

```
Method: GET
EndPoint: /api/users
Request url params: 
	delay: 5

Response:
Time - 5.12 s
{
    "page": 1,
    "per_page": 6,
    "total": 12,
    "total_pages": 2,
    "data": [
        {
            "id": 1,
            "email": "george.bluth@reqres.in",
            "first_name": "George",
            "last_name": "Bluth",
            "avatar": "https://reqres.in/img/faces/1-image.jpg"
        },
        {
            "id": 2,
            "email": "janet.weaver@reqres.in",
            "first_name": "Janet",
            "last_name": "Weaver",
            "avatar": "https://reqres.in/img/faces/2-image.jpg"
        },
        {
            "id": 3,
            "email": "emma.wong@reqres.in",
            "first_name": "Emma",
            "last_name": "Wong",
            "avatar": "https://reqres.in/img/faces/3-image.jpg"
        },
        {
            "id": 4,
            "email": "eve.holt@reqres.in",
            "first_name": "Eve",
            "last_name": "Holt",
            "avatar": "https://reqres.in/img/faces/4-image.jpg"
        },
        {
            "id": 5,
            "email": "charles.morris@reqres.in",
            "first_name": "Charles",
            "last_name": "Morris",
            "avatar": "https://reqres.in/img/faces/5-image.jpg"
        },
        {
            "id": 6,
            "email": "tracey.ramos@reqres.in",
            "first_name": "Tracey",
            "last_name": "Ramos",
            "avatar": "https://reqres.in/img/faces/6-image.jpg"
        }
    ],
    "support": {
        "url": "https://reqres.in/#support-heading",
        "text": "To keep ReqRes free, contributions towards server costs are appreciated!"
    }
}
```

*6. Show single user - invalid*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Single%20User%20-%20Invalid.png)
</details>

```
Method: GET
EndPoint: /api/users/23

Response:
{}
```

*7. Show single <RESOURCE>*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Single%20Resource%20-%20Invalid.png)
</details>

```
Method: GET
EndPoint: /api/unknown/23

Response:
{}
```
*8. Create a user*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Create%20User%20-%20Valid.png)
</details>

```
Method: POST
EndPoint: /api/users
Body:
{
    "name": "morpheus",
    "job": "leader"
}

Response:
{
    "name": "morpheus",
    "job": "leader",
    "id": "806",
    "createdAt": "2022-12-23T17:45:56.469Z"
}
```

*9. Register a user*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Register%20-%20Valid.png)
</details>

```
Method: POST
EndPoint: /api/register
Body:
{
    "email": "eve.holt@reqres.in",
    "password": "pistol"
}

Response:
{
    "id": 4,
    "token": "QpwL5tke4Pnpja7X4"
}
```

*10. Login*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Login%20-%20Valid.png)
</details>

```
Method: POST
EndPoint: /api/login
Body:
{
    "email": "eve.holt@reqres.in",
    "password": "cityslicka"
}

Response:
{
    "token": "QpwL5tke4Pnpja7X4"
}
```

*11. Register a user - invalid*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Register%20-%20Invalid.png)
</details>

```
Method: POST
EndPoint: /api/register
Body:
{
    "email": "sydney@fife"
}

Response:
{
    "error": "Missing password"
}
```

*12. Login - invalid*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Login%20-%20Invalid.png)
</details>

```
Method: POST
EndPoint: /api/login
Body:
{
    "email": "peter@klaven"
}

Response:
{
    "error": "Missing password"
}
```

*13. Update a user*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Update.png)
</details>

```
Method: PUT
EndPoint: api/users/2
Body:
{
    "name": "morpheus",
    "job": "zion resident"
}

Response:
{
    "name": "morpheus",
    "job": "zion resident",
    "updatedAt": "2022-12-23T18:01:18.039Z"
}
```

*14. Update a user*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Update%20(PATCH).png)
</details>

```
Method: PATCH
EndPoint: /api/users/2
Body:
{
    "name": "morpheus",
    "job": "zion resident"
}

Response:
{
    "name": "morpheus",
    "job": "zion resident",
    "updatedAt": "2022-12-23T18:04:24.443Z"
}
```

*15. Delete a user*

<details>
  <summary>Screenshot</summary>
  
  ![Postman](https://github.com/Meiliger/postman/blob/main/reqres.in/Screens/Delete.png)
</details>

```
Method: DELETE
EndPoint: /api/users/2
Response: Stutus: 204 No Content
```

