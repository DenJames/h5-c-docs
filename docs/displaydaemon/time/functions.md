---
sidebar_position: 1
title: API
tags:
 - time
 - epoch
 - C
---

# Time API Overview

This document provides an overview of the time functionality available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `time.h` header file in your source files where time operations are required.

```C
#include "time.h"
```

## Functions

### getTime

This function is used to get the device time in the hh:mm format

```C
extern char* getTime();
```

**Returns:**

- `char`: Returns the time as a string

**Example Usage:**
```C
prinf("The time is %s\n", getTime());
```

### getEpochTime

This function is used to get the current unix/epoch timestamp in UTC

```C
extern int getEpochTime();
```

**Returns:**

- `int`: Returns the current epoch timestamp in the UTC time zone.

**Example Usage:**
```C
prinf("The epoch time is %d\n", getEpochTime());
```

### updateTimeOnDisplay

This function is used to update the LCD display this is an internal project function and should not be in other projects.

```C
extern void* updateTimeOnDisplay();
```

**Returns:**

- `void`

**Example Usage:**
```C
// Remember to include <pthread.h> if you want to use threads
#include <pthread.h>

pthread_t thread;

pthread_create(&thread, NULL, updateTimeOnDisplay, NULL);
```

