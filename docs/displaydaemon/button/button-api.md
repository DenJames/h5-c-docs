---
sidebar_position: 1
title: API
tags:
 - gpio
 - button
 - Blue LED button
 - seeed
 - C
---

# Button Functionality

:::warning
This requires a Blue LED button from seed, and it has to be placed in Digital I/O - GPIO_50 on the Grove Base Cape
:::

This document provides an overview of the Blue LED button functionality available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `button.h` header file in your source files where button operations are required.

```C
#include "button.h"
```

This document will describe the diffrent functions that you can you to get started with the Blue LED button

## Functions

### button_init
This is used to initilise the gpoi pin connection to the button so we can handle button presses
So in the main file you should run this function if you want to use the button in your project.

```C
extern bool button_init();
```

**Returns:**

- `bool`: Returns `true` if the connection is established successfully to the gpio, `false` otherwise.

**Example Usage:**
```C md title="main.c"
if (button_init()) {
    printf("Connection established.\n");
} else {
    fprintf(stderr, "Failed to connect to the button\n");
}

```

### start_button_listener
This is used to start the button press listener, when the button is pressed it will publish a message to mosquito with the tag `alert/cancel` you can then use that to stop the listener or something else.

```C
extern void start_button_listener();
```

**Returns:**

- `void`

**Example Usage:**
```C md title="main.c"
start_button_listener();
```

### stop_button_listener
This is used to stop the button press listener.

```C
extern void stop_button_listener();
```

**Returns:**

- `void`

**Example Usage:**
```C md title="main.c"
start_button_listener();
```

### button_release
This function is used to release the gpio lock so other programs can use it

```C
extern bool button_release();
```

**Returns:**

- `bool`: Returns `true` if the pins got released successfully, `false` otherwise.

**Example Usage:**
```C md title="main.c"
if (button_release()) {
    printf("Button gpio released successfully\n");
} else {
    fprintf(stderr, "Failed to release gpio pins for the button\n");
}
```