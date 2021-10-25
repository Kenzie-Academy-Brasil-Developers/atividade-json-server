# NerdHUB

Está API foi desenvolvida para todos aqueles que querem manter suas nerdices em um único lugar.

## Endpoints

A API tem um total de X endpoints, sendo voltada ao tracking de jogos e filmes favoritos do usuário.

### Cadastro

POST /register <br/>
POST /signup <br/>
POST /users

Qualquer um desses 3 endpoints irá cadastrar o usuário na lista de "Users", sendo que os campos obrigatórios são os de email e password.

`POST /users - FORMATO DA REQUISIÇÃO`

```json
{
	"email": "mbape@mail.com",
	"username": "mbape",
	"password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 201`

```json
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Ikx1aXpSZWlEZWxhc0BtYWlsLmNvbSIsImlhdCI6MTYzNTE5MTE5OCwiZXhwIjoxNjM1MTk0Nzk4LCJzdWIiOiIyIn0.e80d9Uzw-3GUhXc2d60Es00fC1BNM-lSYOehKaFHm7I",
	"user": {
		"email": "LuizReiDelas@mail.com",
		"username": "LuizReiDelas",
		"id": 2
	}
}
```

### Login

POST /login <br/>
POST /signin

Qualquer um desses 2 endpoints pode ser usado para realizar login com um dos usuários cadastrados na lista de "Users"

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
	"email": "mbape@mail.com",
	"password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /users - FORMATO DA RESPOSTA - STATUS 200`

```json
{
	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6Ikx1aXpSZWlEZWxhc0BtYWlsLmNvbSIsImlhdCI6MTYzNTE5MTE5OCwiZXhwIjoxNjM1MTk0Nzk4LCJzdWIiOiIyIn0.e80d9Uzw-3GUhXc2d60Es00fC1BNM-lSYOehKaFHm7I",
	"user": {
		"email": "LuizReiDelas@mail.com",
		"username": "LuizReiDelas",
		"id": 2
	}
}
```

### Games

POST /games
GET /games

`POST /games - FORMATO DA REQUISIÇÃO`

> Authorization: Bearer {token}

```json
{
	"name": "Counter Strike: Global Offensive",
	"skill": "Low",
	"userId": 2
}
```

Caso dê tudo certo, a resposta será assim:

`POST /games - FORMATO DA RESPOSTA - STATUS 200`

```json
{
	"name": "Counter Strike: Global Offensive",
	"skill": "Low",
	"userId": 2,
	"id": 2
}
```

`GET /games - FORMATO DA RESPOSTA - STATUS 200`

Essa rota não precisa de autorização portanto é necessário apenas fazer a requisição para se ter acesso aos dados da API

```json
[
	{
		"name": "League of Legends",
		"skill": "Low",
		"userId": 2,
		"id": 1
	},
	{
		"name": "Counter Strike: Global Offensive",
		"skill": "Low",
		"userId": 2,
		"id": 2
	}
]
```

### Movies

POST /movies
GET /movies

`POST /movies - FORMATO DA REQUISIÇÃO`

Está rota precisa de um Auth token para o envio dos dados

> Authorization: Bearer {token}

```json
{
	"title": "Star Wars Episode IV: A New Hope",
	"year": "1977"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /movies - FORMATO DA RESPOSTA - STATUS 201`

```json
{
	"title": "Star Wars Episode IV: A New Hope",
	"year": "1977",
	"id": 3
}
```

`GET /movies - FORMATO DA REQUISIÇÃO`

Essa rota precisa de um Auth token para que você possa ver os dados

> Authorization: Bearer {token}

`GET /movies - FORMATO DA RESPOSTA - STATUS 200`

```json
[
	{
		"title": "Interestelar",
		"year": "2014",
		"id": 1
	},
	{
		"title": "Matrix",
		"year": "1999",
		"id": 2
	},
	{
		"title": "Star Wars Episode IV: A New Hope",
		"year": "1977",
		"id": 3
	}
]
```
