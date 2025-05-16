# Cybersecurity : CSN150-Doc-Template

## Name of Project
ESP32 Introduction

## Purpose
Set up ESP32 and Arduino enviornment. Execute sketch " Wifiscanner". 

## Equipment
* [ESP32Cam](https://www.amazon.com/Aideepen-ESP32-CAM-Bluetooth-ESP32-CAM-MB-Arduino/dp/B08P2578LV/ref=sr_1_3?crid=4FY0ECFW0ZX7&keywords=ESP32+Cam&qid=1678902050&sprefix=esp32+cam%2Caps%2C240&sr=8-3)

* [USB Micro Data Cable](https://www.amazon.com/AmazonBasics-Male-Micro-Cable-Black/dp/B0711PVX6Z/ref=sr_1_1_sspa?keywords=micro+usb+data+cable&qid=1678902214&sprefix=Micro+USB+data+%2Caps%2C89&sr=8-1-spons&psc=1&spLa=ZW5jcnlwdGVkUXVhbGlmaWVyPUFaU0NaUVZHU1RFUlAmZW5jcnlwdGVkSWQ9QTA3NTA4MDVFVERCS01HVlgxM1YmZW5jcnlwdGVkQWRJZD1BMDE4NTE1NTIwWUdONkdWSzU1M1Amd2lkZ2V0TmFtZT1zcF9hdGYmYWN0aW9uPWNsaWNrUmVkaXJlY3QmZG9Ob3RMb2dDbGljaz10cnVl)

## Prerequisites
ESP32-CAM (AI Thinker)

ESP32-CAM MB USB Programmer (for easier flashing)

Micro USB cable

PlatformIO installed in VS Code


## Steps I followed
1. PlatformIO Project Setup
Open VS Code and create a new PlatformIO project.

Select Espressif ESP32 as the platform and AI Thinker ESP32-CAM as the board.

Configure the platformio.ini file as follows:
[env:esp32cam]
platform = espressif32
board = esp32cam
framework = arduino
upload_speed = 921600
monitor_speed = 921600
build_flags = -D LED_BUILTIN=4

2. Writing the Code
Copy and paste the following code into your main.cpp file:
#include <Arduino.h>

#define LED_BUILTIN 4

void setup() {
  pinMode(LED_BUILTIN, OUTPUT);
  Serial.begin(921600);
  Serial.println("This is a drill");
}

void loop() {
  delay(1000);
  digitalWrite(LED_BUILTIN, HIGH);
  Serial.println("This is a drill");
  delay(1000);
  digitalWrite(LED_BUILTIN, LOW);
}

3. Uploading & Testing
Connect the ESP32-CAM MB to USB.

Hold down the BOOT button while initiating the upload in PlatformIO.

Open the Serial Monitor at 921600 baud and observe the output.

If successful, the LED will blink, and "This is a drill" will print every second.

## Problems

"Failed to connect to ESP32: Timed out waiting for packet header"

This happens when the ESP32 can't enter programming mode. A charge-only cable (without data lines) can prevent proper communication.

How to Fix It?
Use a high-quality, data-capable USB cable (some cables are only for charging!).

Try a different USB port or a powered hub.

Ensure drivers for the ESP32’s USB-to-serial converter are correctly installed.




## Final Report
Key Accomplishments
Project Initialization:

Successfully forked and customized the setup process for the ESP32-CAM using the AI Thinker board.

Configured PlatformIO with appropriate parameters for smooth operation.

Firmware Development:

Implemented and tested LED control using GPIO 4.

Integrated Serial.begin(921600) for high-speed debugging output.

Added test messaging "This is a drill" to confirm proper execution.

Uploading and Debugging:

Used correct boot sequence for flashing the ESP32-CAM MB.

Addressed potential cable-related errors and ensured proper connections.

Validated successful operation through Serial Monitor output and LED behavior.

Challenges & Resolutions
USB Cable Issues: Identified potential connectivity problems with charge-only cables and replaced them with reliable data-capable cables.

Flash Mode Activation: Ensured manual boot button press during upload to resolve timeout errors.

Baud Rate Optimization: Used 921600 baud for faster serial communication without data corruption.

Future Improvements
Expand documentation to include camera initialization and Wi-Fi connectivity.

Create troubleshooting flowcharts for common ESP32-CAM errors.

Automate firmware deployment for streamlined testing.
