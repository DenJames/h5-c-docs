---
sidebar_position: 1
title: API
tags:
 - i2c
 - C
---

# I2C API Overview

This document provides an overview of the I2C functionality available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `i2c.h` header file in your source files where I2C operations are required.

```C
#include "i2c.h"
```

## Functions

### i2c_init

This function is used to connect to the I2C device.

```C
extern char i2c_init(unsigned int address, char *bus);
```

**Parameters:**

- `address`: A integer representing the address of the i2c device.
- `bus`: A string representing the I2C bus/file.

**Returns:**

- `char`: Returns the file handle pointrer.

**Example Usage:**
```C
int file;
// Attempts to initialize a connection to the i2c bus and returns a file pointer.
file = i2c_init("/dev/i2c-2", 0x3e);
```

### write_to_buff

```C
extern bool write_to_buff(int bus, uint8_t buf[], int amount);
```

**Parameters:**

- `bus`: A (file pointer/int) representing the file handler to write to.
- `buf`: A integer array representing the bits to write to the i2c device.
- `amount`: A integer representing the abount of bits to write to the i2c device.

**Returns:**

- `bool`: Returns `true` if the operation is successful, `false` otherwise.

**Example Usage:**
```C
// Attempts to write the data to the i2c device.
uint8_t buf[2] = {0x00, 0x01};
int file;
file = i2c_init("/dev/i2c-2", 0x3e);
if (write_to_buff(file, buf, 2)) {
    printf("Data write successful.\n");
} else {
    fprintf(stderr, "Error writing data to i2c device\n");
}
```

### write_to_buff

```C
extern bool read_from_buff(int bus, char *buf, int amount);
```

**Parameters:**

- `bus`: A (file pointer/int) representing the file handler to read from.
- `buf`: A string pointer to write the data to from the i2c device.
- `amount`: A integer representing the abount of bits to read from the i2c device.

**Returns:**

- `bool`: Returns `true` if the operation is successful, `false` otherwise.

**Example Usage:**
```C
// Attempts to read the data from the i2c devie, and returns a char buffer array.
char buf[2];
int file;
file = i2c_init("/dev/i2c-2", 0x18);
if (read_from_buff(file, buf, 2);) {
    printf("Data read successfully.\n");
} else {
    fprintf(stderr, "Error reading data from the i2c device\n");
}
```

