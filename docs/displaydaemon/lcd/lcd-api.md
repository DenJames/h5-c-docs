---
sidebar_position: 1
title: API
---

# LCD Grove API Overview

:::warning
This requires an LCD display to be placed on your BBB
:::

This document provides an overview of the LCD Display API available in our project. It is intended to help developers understand and use the API effectively.

Before using the functions described below, ensure to include the `Grove_LCD.h` header file in your source files where database operations are required.

```c
#include "Grove_LCD.h"
```

## Functions


### display_init

Initializes the display by setting up the I2C communication & configuring display settings.

```C
extern void display_init();
```

**Returns:**

- `void`

**Usage:**
```C
// Use this to call the display_init method
display_init();
```

**Display init declaration**

```C
// Example of how we can define the display init method
void display_init() {
  file = i2c_init(LCD_ADR, I2C_BUS);
  color_bus = i2c_init(LCD_COLOR_BUS, I2C_BUS);

  buf[0] = 0x00;
  buf[1] = 0x28;
  write_to_buff(file, buf, 2);

  buf[1] = 0x0C;
  write_to_buff(file, buf, 2);

  buf[1] = 0x01;
  write_to_buff(file, buf, 2);

  buf[1] = 0x06;
  write_to_buff(file, buf, 2);

  buf[1] = 0x02;
  write_to_buff(file, buf, 2);
}
```

### display_write_line
Writes a string of text to the current cursor position on the display.

```C
extern void display_write_line(char string[]);
```

**Parameters:**
- `string`: The text to display on the LCD.

**Returns:**

- `void`

**Usage:**
```C
// Writes "Hello, World!" to the current cursor position
display_write_line("Hello, World!");
```

### display_change_line
Changes the cursor position to the specified line and position.

```C
extern void display_change_line(int line, int pos);
```

**Parameters:**
- `line`: The line number on the display (1 or 2).
- `pos`: The position on the line (starting from 0 ranging to 16).

**Returns:**

- `void`

**Usage:**
```C
// Moves the cursor to the beginning of the second line
display_change_line(2, 0);
```

### display_clear

Clears the display screen.

```C
extern void display_clear();
```

**Returns:**

- `void`

**Usage:**
```C
display_clear();
```


### display_color
Changes the background color of the display.

```C
extern void display_color(uint8_t color);
```

**Parameters:**
- `color`: The color value to set the display background to.

**Returns:**

- `void`

**Usage:**
```C
// Sets the display background color to blue
display_color(0x05)
```

## Error Handling

When intefering with the display, ensure to check the return values of i2c_init and write_to_buff functions for a successful operation. The mutex locks within display_write_line function help in thread-safe operations when dealing with I2C communication.

Make sure to handle I2C errors appropriately by checking for failed initializations or write operations and taking necessary corrective actions.

These functions provide a high-level API for interacting with the Grove LCD display, abstracting away the lower-level details of I2C communication.
