# AWS IoTCore

## What is it?

- Cloud service that lets iot devices connect and communicate with AWS cloud apps and services

## Features

| Secure Communication | Uses MQTT, HTTPS, and WebSockets with TLS encription |
| --- | --- |
| Device Registry | Manage millions of devices |
| Device shadows | Creates a virtual copy of a devices state so it can be tracked or updated even when offline |
| Rules engine | automatically routes device data to other AWS services (S3, Lambda, SNS etc) |
| Pub/Sub Messaging | Devices publish data or subscribe to topics via MQTT |
| Auth | Devices auth with X.509 certificates, IAM, or cognito |
|  |  |

## How it works

- Device connect to AWS IoT Core view MQTT or HTTPS
- Device publishes a message to a topic like sensors/temperature
- Rules Engine Triggers and routes data to a Lambda function, database, or storage bucket
- App pr Cloud responds by sending control messages back to the device

[How would IoT Core be used to manage autonomous grills?](AWS%20IoTCore%201f3b5acef1a1804e9acfdc90b204b4b4/How%20would%20IoT%20Core%20be%20used%20to%20manage%20autonomous%20gr%201f4b5acef1a180c6ac82c34891080ea5.md)