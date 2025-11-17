
# Ticket Control System - Official API

A robust REST API for managing ticket sales, departments, and ticket types with OAuth 2.0 authentication.

@owner:
</br>
<img style="width: 100px" src="http://kfkserwis.pl/wp-content/uploads/2020/11/kfk.png">
</br>
http://kfkserwis.pl/

@author:
</br>
<img style="width: 100px" src="https://schdeveloper.pl/images/logotyp_SCH.png">
</br>
https://schdeveloper.pl/

___

## Very Quick Start 
Check postman json file for request examples

## Quick Start
 
1. Contact with support to get your credentials (support ask for server address IP which make request)
2. Obtain an access token
```shell
curl -X POST http://localhost/oauth/token \
     -H "Content-Type: application/json" \
     -d '{
       "grant_type": "password",
       "client_id": "YOUR_CLIENT_ID",
       "client_secret": "YOUR_CLIENT_SECRET",
       "username": "YOUR_EMAIL",
       "password": "YOUR_PASSWORD"
     }'
```
3. Get departments
```shell
curl -X POST http://localhost/api/departments \
     -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
     -H "Accept: application/json"
```
*Response:*
```json
{
    "success": true,
    "data": [
        {
            "department_id": 2, // use this id in ticket purchase endpoint
            "name": "MPK Warszawa" 
        }
    ]
}
```
4. Get ticket types
```shell
curl -X POST http://localhost/api/ticket-types \
```

*Response:*
```json
{
  "success": true,
  "data": [
    {
      "id": 59, // use this id in ticket purchase endpoint
      "name": "1 przejazdowy",
      "description": "opis...",
      "price": 1.5,
      "duration": 1,
      "duration_unit": "przejazd",
      "ticket_type_code": "1_przejazdowy"
    }
  ]
}
```
5.Buy a ticket
```shell
curl -X POST http://localhost/api/tickets/buy \
     -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \
     -H "Content-Type: application/json" \
     -H "Accept: application/json" \
     -d '{
       "ticket_type_id": 59, // selected ticket_type_id from 4th step
       "department_id": 2 // selected department_id from 3rd step
     }'
 ```

___

## 🎯 Overview

The Ticket Control System API provides a comprehensive solution for managing ticket sales, user departments, and ticket type configurations. Built with security in mind, it uses OAuth 2.0 password grant flow for authentication.

## ✨ Features

- **OAuth 2.0 Authentication** - Secure token-based authentication with refresh token support
- **Department Management** - Retrieve and manage user departments
- **Ticket Types** - Query available ticket types with pricing and duration information
- **Ticket Purchase** - Buy tickets with automatic QR code generation
- **Provider-based Access Control** - Ticket types restricted by provider

## 🔐 Authentication

This API uses **OAuth 2.0** with password grant type. All authenticated endpoints require a Bearer token in the Authorization header.

### Getting an Access Token

**Endpoint:** `POST /oauth/token`

**Request Body:**
```json
{
    "grant_type": "password",
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET",
    "username": "YOUR_EMAIL",
    "password": "YOUR_PASSWORD",
    "scope": ""
}
```
**Response** 
```json
{
  "access_token": "...",
  "refresh_token": "...",
  "token_type": "Bearer",
  "expires_in": 3600
}
```

### Getting an Access Token

**Endpoint:** `POST /oauth/token`

**Request Body:**

```json
{
    "grant_type": "refresh_token",
    "refresh_token": "YOUR_REFRESH_TOKEN",
    "client_id": "YOUR_CLIENT_ID",
    "client_secret": "YOUR_CLIENT_SECRET",
    "scope": "*"
}
```


### Using the Token
```
Authorization: Bearer YOUR_ACCESS_TOKEN
```


##  Support

For support, please contact [your-email@example.com] or open an issue in this repository.