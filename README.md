
# Ticket Control System - Official API

A robust REST API for managing ticket sales, departments, and ticket types with OAuth 2.0 authentication.

@owner:
</br>
<img  style="width: 100px" src="http://kfkserwis.pl/wp-content/uploads/2020/11/kfk.png">
</br>
http://kfkserwis.pl/

@author:
</br>
<img style="width: 100px" src="https://schdeveloper.pl/images/logotyp_SCH.png">
</br>
https://schdeveloper.pl/


## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Authentication](#authentication)
- [Base URL](#base-url)
- [Endpoints](#endpoints)
    - [Authentication](#authentication-endpoints)
    - [Departments](#departments-endpoints)
    - [Ticket Types](#ticket-types-endpoints)
    - [Tickets](#tickets-endpoints)
- [Response Format](#response-format)
- [Error Handling](#error-handling)
- [Postman Collection](#postman-collection)
- [Getting Started](#getting-started)

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