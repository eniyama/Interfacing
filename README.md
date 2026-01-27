# USB Webcam Interfacing & Image Capture on Raspberry Pi 4

This repository explains how to interface a **USB webcam** with a **Raspberry Pi 4 Model B**, capture an image using command-line tools, and display or view the captured image.

---

## Hardware Requirements
- Raspberry Pi 4 Model B
- USB Webcam (UVC compatible – e.g. Logitech B525, C615)
- Power adapter for Raspberry Pi
- HDMI display & keyboard (optional)
- PC/Laptop for SSH (optional)

---

## Software Requirements
- Raspberry Pi OS (32-bit or 64-bit)
- Internet connection
- SSH enabled (optional)

---

## Step 1: Connect Webcam to Raspberry Pi
1. Power OFF the Raspberry Pi
2. Connect the USB webcam to any USB port
3. Power ON the Raspberry Pi

---

## Step 2: Verify Webcam Detection

### Check USB devices
```bash
lsusb

Expected 
Bus 001 Device 007: ID 046d:0836 Logitech, Inc. B525 HD Webcam

## Install Required Tool

### Tool Used
- **fswebcam**
- Uses **V4L2 (Video4Linux2)** to capture images

### Install fswebcam
```bash
sudo apt update
sudo apt install fswebcam

## Capture Image from Webcam

### Basic capture
```bash
fswebcam test.jpg

### Specify Device Explicitly
```bash
fswebcam -d /dev/video0 test.jpg


## Display Image Using ImageMagick (X Server)

If GUI tools like `eom` are not available, the image can be displayed using **ImageMagick**.

---

### Step 1: Try Display Command

```bash
display image.jpg

If you get the error:
-bash: display: command not found

### Step 2: Install ImageMagick
sudo apt update
sudo apt install imagemagick

### Step 3: Start X Server (GUI Required)

```bash
startx

This requires:
HDMI display connected to Raspberry Pi
Keyboard/mouse connected
Proper user permissions

### Step 4: Display the Image
```bash
display name.jpg

Tools & Libraries Used
| Purpose         | Tool / Library |
| --------------- | -------------- |
| Image Capture   | fswebcam       |
| Video Interface | V4L2           |
| Image Display   | ImageMagick    |
| GUI Environment | X.Org Server   |

