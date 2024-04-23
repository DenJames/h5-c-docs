---
sidebar_position: 1
title: Config
tags:
 - variables
 - Header
 - .h
 - C
---
:::note
This is the configuration file where you can specify the diffrent variables for the program, and not functions.
:::

```C md title="constants.h"
// LCD
#define DISPLAY_COLOR_CODE 0x05
#define LCD_ADR 0x3e
#define LCD_COLOR_BUS 0x62

// IP
#define ETHERNET_INTERFACE "eth0"

// MCP9808
#define I2C_BUS "/dev/i2c-2"


// MySQL
#define MYSQL_HOST "85.203.138.42"
#define MYSQL_PORT 3306
#define MYSQL_USER "temp"
#define MYSQL_PASSWORD "temp"
#define MYSQL_DATABASE "H5"

// MQTT
#define MQTT_HOST "85.203.138.42"
#define MQTT_PORT 53
#define MQTT_PUBLISH_TAG "bbb/002/celcius"
#define MQTT_RETAIN true
#define MQTT_QOS 0
```

### DISPLAY_COLOR_CODE
This is used to specify the primary color of the Grove LCD Display and it goes between 0x00 to 0x15

0x10 RED

0x01 BLUE

0x04 GREEN

0x15 RGB = White (Sort of)

### LCD_ADR
This is the i2c address for the display chip

### LCD_COLOR_BUS
This is the i2c address for the display color chip

### ETHERNET_INTERFACE
This is the network interface to get the ip from. To get a list if interfaces type `ip a` or `ifconfig` if you have net-tools installed

### I2C_BUS
This is where you specify the i2c file location on the file system

### MySQL
<details>
  <summary>MYSQL_HOST</summary>
  <div>
    <div>Here you can specify the mysql host/ip <code>127.0.0.1</code> or <code>database.local</code></div>
  </div>
</details>
<details>
  <summary>MYSQL_PORT</summary>
  <div>
    <div>This is the port of your mysql database. Default <code>3306</code></div>
  </div>
</details>
<details>
  <summary>MYSQL_USER</summary>
  <div>
    <div>This is the username of the database user. Default <code>root</code></div>
  </div>
</details>
<details>
  <summary>MYSQL_PASSWORD</summary>
  <div>
    <div>This is the password for the mysql user. By default the root user dosent have a password if its local</div>
  </div>
</details>
<details>
  <summary>MYSQL_DATABASE</summary>
  <div>
    <div>This is the database to connect to. There is no default you have to create one</div>
  </div>
</details>

### MQTT
<details>
  <summary>MQTT_HOST</summary>
  <div>
    <div>Here you can specify the mosquitto host/ip <code>127.0.0.1</code> or <code>mosquitto.local</code></div>
  </div>
</details>
<details>
  <summary>MQTT_PORT</summary>
  <div>
    <div>This is the port of your mosquitto. Default <code>1883</code></div>
  </div>
</details>
<details>
  <summary>MQTT_PUBLISH_TAG</summary>
  <div>
    <div>This is the tag mosquitto will publish on. Default <code>bbb/002/celcius</code></div>
  </div>
</details>
<details>
  <summary>MQTT_RETAIN</summary>
  <div>
    <div>This is used to retain mosquitto messages from the program. Default <code>0</code></div>
  </div>
</details>
<details>
  <summary>MQTT_QOS</summary>
  <div>
    <div>This is the quality of service for the messages 0 means just send, 1 means send and recive ack and 2 means send it once and no more</div>
  </div>
</details>