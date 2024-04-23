---
sidebar_position: 1
title: API
---

# MariaDB Functionality

This document provides an overview of the MariaDB functionality available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `mariadb.h` header file in your source files where database operations are required.

```C
#include "mariadb.h"
```

## Functions

### mariadb_connect

This function is used to establish a connection to a MariaDB database.

```C
extern bool mariadb_connect(char *host, char *user, char *password, char *database, int port);
```

**Parameters:**

- `host`: A string representing the hostname of the MariaDB server.
- `user`: A string representing the username to log in as.
- `password`: A string representing the password to use.
- `database`: A string representing the name of the database to connect to.
- `port`: An integer representing the port number to connect to.

**Returns:**

- `bool`: Returns `true` if the connection is established successfully, `false` otherwise.

**Example Usage:**
```C
if (mariadb_connect("localhost", "db_user", "db_pass", "my_db", 3306)) {
    printf("Connection established.\n");
} else {
    fprintf(stderr, "Failed to connect: %s\n", mysql_error(conn));
}

```

### mariadb_insert

```C
extern bool mariadb_insert(char *query);
```

**Parameters:**

- `query`: A string representing the SQL query to execute.

**Returns:**

- `bool`: Returns `true` if the connection is established successfully, `false` otherwise.

**Example Usage:**
```C
char *query = "INSERT INTO users (username, age) VALUES ('john_doe', 30);";
if (mariadb_insert(query)) {
    printf("Data inserted successfully.\n");
} else {
    fprintf(stderr, "Insert failed: %s\n", mysql_error(conn));
}

