---
sidebar_position: 1
title: Header
tags:
 - gpio
 - button
 - Blue LED button
 - seeed
 - C
---

# Functions
:::danger
This requires a Blue LED button from seed, and it has to be placed in Digital I/O - GPIO_50 on the Grove Base Cape
:::

This document will describe the diffrent functions that you can you to get started with the Blue LED button

```C md title="button.h"
extern bool button_release();
extern bool button_init();
extern void start_button_listener();
extern void stop_button_listener();
```

# button_init();
This is used to initilise the gpoi pin connection to the button so we can handle button presses
So in the main file you should run this function if you want to use the button in your project.
```C md title="main.c"
#include <stdio.h>

#include "button.h"

int main(void) {
  if (!button_init()) {
    return 0;
  }
  ... code
}
```

# start_button_listener();
This is used to start the button press listener, when the button is pressed it will publish a message to mosquito with the tag `alert/cancel` you can then use that to stop the listener or something else.

```C md title="main.c"
#include <stdio.h>

#include "button.h"

int main(void) {
  if (!button_init()) {
    return 0;
  }
  start_button_listener();
  ... code
}
```

# stop_button_listener();
This is used to stop the button press listener.
```C md title="main.c"
#include <stdio.h>
#include <unistd.h>

#include "button.h"

int main(void) {
  if (!button_init()) {
    return 0;
  }
  start_button_listener();
  sleep(5) # sleep 5 secounds
  stop_button_listener();
  ... code
}
```

# button_release();
This function is used to release the gpio lock so other programs can use it

```C md title="main.c"
#include <stdio.h>
#include <unistd.h>

#include "button.h"

int main(void) {
  if (!button_init()) {
    return 0;
  }
  start_button_listener();
  sleep(5) # sleep 5 secounds
  stop_button_listener();
  if (!button_release()) {
    return 0;
  }
  ... code
}
```