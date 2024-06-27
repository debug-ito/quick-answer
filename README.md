# quick-answer

This is a program for [M5Stack Core2](https://shop.m5stack.com/products/m5stack-core2-esp32-iot-development-kit) devices.
Using the devices with this program, you can quickly tell your partner if you are gonna answer the doorbell (or not).

The program is developed with [UIFlow](https://m5stack.com/uiflow) framework at https://flow.m5stack.com

## How it works

<img src="devices.jpg" width="600" />

This program runs on a pair of devices.
You keep one of them, while your partner keeps the other.

Each device has two buttons ("O" and "X") on the lower side of the screen.

- Pressing "O" indicates that you are OK (e.g., you can answer the doorbell.)
- Pressing "X" indicates that you are not OK (e.g., you cannot answer the doorbell.)

When you press the button, your intension is shown in your partner's device (in the upper side of the screen.)

By default, when you don't touch the button for a while, both buttons will go back to grey. Your partner's device will show "?", meaning that your intension is unknown.

The above behavior is changed if you check the "Keep" box by pressing it.
If the "Keep" box is checked, the buttons won't go back to grey automatically, but they keep its current state.
If you want to reset the button's state, just press it again.

Under the hood, the two devices communicate with each other over Wi-Fi and a MQTT broker.

## How to use

- Prepare two M5Stack Core2 devices and a MQTT broker.
- Follow [this guide](https://docs.m5stack.com/en/uiflow/uiflow_web) to set up UIFlow on those devices. This includes the following steps.
  - Install the M5Burner tool on your development PC.
  - Burn the `UIFlow_Core2` firmware on the devices (see the [manual](https://docs.m5stack.com/en/uiflow/m5core2/program)). You should also configure Wi-Fi settings at this step.
- Access UIFlow service ( https://flow.m5stack.com ) by your development PC.
- Open [quick-answer.m5f](quick-answer.m5f) file.
- Configure parameters.
  - `mqtt_client_id`: the ID of your device. Any string is ok, as long as it's different from `partner_client_id`.
  - `partner_client_id`: the ID string of your partner's device.
  - `mqtt_server_address`: the hostname or address of the MQTT server (broker).
  - `mqtt_server_port`: the port number of the MQTT server.
  - `mqtt_user_name`: the user name for accessing the MQTT server.
  - `mqtt_password`: the password for accessing the MQTT server.
- Download the firmware into your device.
- Swap `mqtt_client_id` and `partner_client_id` and download the firmware into your partner's device.

## Author

Toshio Ito <debug.ito@gmail.com>

