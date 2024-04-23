---
sidebar_position: 1
title: API
---

# MQTT Communication API

This document outlines the MQTT communication functions available in our project, aimed at enabling seamless message publishing and subscription using the MQTT protocol.

Before using these functions, ensure to include the `mqtt.h` header file in your source files.

```c
#include "mqtt.h"
```

## Functions

### mqtt_connect

```C title="mqtt.h"
extern bool mqtt_connect(char *host, int port);
```

**Parameters:**
- `host`: The hostname or IP address of the MQTT broker.
- `port`: The network port of the MQTT broker, typically 1883 for non-TLS communication.

**Returns:**

- `bool`: Always returns true currently, but should be updated to reflect the actual success of the connection attempt.

**Usage:**
```C
// Attempt to connect to the MQTT broker
if (mqtt_connect("broker.example.com", 1883)) {
    printf("Connected to MQTT broker.\n");
} else {
    fprintf(stderr, "Failed to connect to MQTT broker.\n");
}
```

### publish_message

```C title="mqtt.h"
extern bool publish_message(char *message, char *topic, int qos, bool retain);
```

**Parameters:**
- `message`: The message payload to publish.
- `topic`: The topic on which the message should be published. 
- `qos`: The Quality of Service level to apply to the message.
- `retain`: Whether the message should be retained by the broker.

**Returns:**

- `bool`: Returns true if the message is successfully published, false if the publishing fails.

**Usage:**
```C
// Publish a message with QoS level 1 and no retain flag
bool success = publish_message("Hello MQTT", "test/topic", 1, false);
if (success) {
    printf("Message published.\n");
} else {
    fprintf(stderr, "Failed to publish message.\n");
}
```