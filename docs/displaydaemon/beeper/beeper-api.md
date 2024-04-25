---
sidebar_position: 1
title: API
tags:
 - gpio
 - beeper
 - seeed
 - C
 - Buzzer v1.2
---

# Beeper API Overview

:::warning
This requires a Buzzer v1.2 from seed, and it has to be placed in Digital I/O - GPIO_115 on the Grove Base Cape
:::

This document provides an overview of the Buzzer v1.2 functionality available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `beeper.h` header file in your source files where button operations are required.

```C
#include "beeper.h"
```

This document will describe the diffrent functions that you can you to get started with the Buzzer v1.2

## Functions

### beeper_init
This is used to initilise the gpoi pin connection to the Buzzer so we can make an awful sound
So in the main file you should run this function if you want to use the Buzzer in your project.

```C
extern bool beeper_init();
```

**Returns:**

- `bool`: Returns `true` if the connection is established successfully to the gpio, `false` otherwise.

**Example Usage:**
```C md title="main.c"
if (beeper_init()) {
    printf("Connection established.\n");
} else {
    fprintf(stderr, "Failed to connect to the Buzzer\n");
}

```

### start_beeper
This is used to start the Buzzer to make the awful sound, nothing else just there to annoy you.

```C
extern void start_beeper();
```

**Returns:**

- `void`

**Example Usage:**
```C md title="main.c"
start_beeper();
```

### stop_beeper
This is used to stop the Buzzer.

```C
extern void stop_beeper();
```

**Returns:**

- `void`

**Example Usage:**
```C md title="main.c"
stop_beeper();
```

### beeper_release
This function is used to release the gpio lock so other programs can use it

```C
extern bool beeper_release();
```

**Returns:**

- `bool`: Returns `true` if the pins got released successfully, `false` otherwise.

**Example Usage:**
```C md title="main.c"
if (beeper_release()) {
    printf("Buzzer gpio released successfully\n");
} else {
    fprintf(stderr, "Failed to release gpio pins for the Buzzer\n");
}
```