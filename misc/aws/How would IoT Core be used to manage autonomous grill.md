# How would IoT Core be used to manage autonomous grills?

- Each grill connects to AWS Iot core through wifi or cellular using MQTT and is registered in the device registry with its own identity and certificates
- Real Time Telemetry
    - Grill would publish data to a topic like grills/grill_id/status w a structure like
        
        ```jsx
        {
          "temperature": 375,
          "target_temp": 400,
          "burner_state": "on",
          "lid_closed": true,
          "meat_probe_temp": 145
        }
        ```
        
    - The data can be routed with rules engine to Lambda for real time processing for an alert if something is wrong
- From the central app, the user can send commands like
    
    ```jsx
    {
      "target_temp": 425,
      "burner_state": "off"
    }
    ```
    
    - commands would be published to grills/grill_id_command. The grill subscribes to this topic
- Device Shadow for Offline sync
    - If a grill goes offline, the device shadow stores the desired state (eg-target temp = 400) and when it reconnects, it checks the shadow and sees the difference (delta) and adjusts
    - **Lambda + ML Model can optimise grill behavior**
        - Predictive Shutdown: turn off grill before it overheats or runs dry
        - Fuel efficiency optimization
    - Cloud watch alarm — monitoring service in AWS that collects metrics (like temp, CPU usage etc), logs and events from AWS resources and iot devices.
        - Its A trigger that watches a specific metric and takes action when it crosses a thresold
        - “If grill temperature exceeds 500°F for more than 2 minutes → trigger alarm.” Then it can send a notification via SNS or trigger an AWS lambda function to turn off the grill via MQTT, and log the event for safety or debugging