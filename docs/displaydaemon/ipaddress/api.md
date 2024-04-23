---
sidebar_position: 1
title: API
---

# IPAddress API

This document outlines the MQTT communication functions available in our project, aimed at enabling seamless message publishing and subscription using the MQTT protocol.

Before using these functions, ensure to include the `IpAddress.h` header file in your source files.

```c
#include "IpAddress.h"
```

## Functions

### IPAddress

```C title="IpAddress.h"
extern char* IPAddress(char *interface);
```

**Parameters:**
- `interface`: The name of the network interface (e.g., "eth0") from which to retrieve the IP address.

**Returns:**

- `char*`: The IP address as a string in dotted decimal format. Returns NULL if the IP address cannot be retrieved.

**Usage:**
```C
/* Example usage in main.c or any other .c file */
#include "IPAddress.h"

char *ip = IPAddress("eth0");
if (ip) {
    printf("IP Address: %s\n", ip);
} else {
    fprintf(stderr, "Failed to retrieve IP address.\n");
}
```

### publish_message

```C title="IpAddress.h"
extern void* updateIpaddressOnDisplay();
```

**Returns:**

- `void*`

**Usage:**
```C
// This function is designed to be run in a separate thread,
// constantly updating the display with the IP address.
pthread_t ip_display_thread;
pthread_create(&ip_display_thread, NULL, updateIpaddressOnDisplay, NULL)
```


## Constants and System Calls

In the IPAddress implementation, several constants and system calls are used:

- ``IFNAMSIZ``: This constant defines the maximum buffer size that can be used for a network interface's name. In the context of the ifreq structure, this size is used to ensure the interface name does not exceed the maximum allowed length.

- ``AF_INET``: This constant is used to denote the address family for IPv4 addresses.

- ``SOCK_DGRAM``: This constant is used to specify the type of socket created, which in this case is a datagram socket used for UDP.

- ``SIOCGIFADDR``: This ioctl command is used to get the address of the device using the ifreq structure.

- ``inet_ntoa()``: This function converts an IP address in a struct in_addr to a string in dotted decimal format.

These constants and system calls are integral to networking in Unix-like systems, providing standardized ways to interact with network interfaces and addresses.