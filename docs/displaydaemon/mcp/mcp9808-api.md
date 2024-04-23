---
sidebar_position: 1
title: API
tags:
 - C
 - MCP9808
 - Temperature sensor
 - i2c
 - Header
 - seeed
 - Grove I2C High Accuracy Temerature Sensor
 - Grove
---

# MCP9808 API Overview

:::warning
This requires a Grove I2C High Accuracy Temerature Sensor from seed, and it has to be placed in the first I2C_2 on the Grove Base Cape
:::

This document provides an overview of the MCP9808 functionality available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `MCP9808.h` header file in your source files where temperature operations are required.

```C
#include "MCP9808.h"
```

## Functions

### MCP9808_read

This function is used to get the temperature from the Grove I2C High Accuracy Temerature Sensor

```C
extern float MCP9808_read();
```

**Returns:**

- `float`: Returns the temperature as a float

**Example Usage:**
```C
prinf("The temperature is %.5f\n", MCP9808_read());
```

### MCP9808_init

Initializes the High Accuracy Temerature Sensor by setting up the I2C communication

```C
extern void MCP9808_init();
```

**Returns:**

- `void`

**Example Usage:**
```C
MCP9808_init();
```

### updateTempOnDisplay

This function is used to update the LCD display temperature, this is an internal project function and should not be in other projects.

```C
extern void* updateTempOnDisplay();
```

**Returns:**

- `void`

**Example Usage:**
```C
// Remember to include <pthread.h> if you want to use threads
#include <pthread.h>

pthread_t thread;

pthread_create(&thread, NULL, updateTempOnDisplay, NULL);
```

