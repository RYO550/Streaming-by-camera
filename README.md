# Streaming by Camera on Raspberry Pi

This project demonstrates how to stream video from a camera connected to a Raspberry Pi.

## Prerequisites

- Raspberry Pi with a camera (e.g., Pi Camera or USB webcam)
- Installed GStreamer on Raspberry Pi
- Ubuntu or other Linux distribution on your client PC

### Step 1: Install GStreamer on Raspberry Pi

Run the following commands to install GStreamer on Raspberry Pi:

```bash
sudo apt update
sudo apt install gstreamer1.0-tools gstreamer1.0-plugins-base gstreamer1.0-plugins-good gstreamer1.0-plugins-bad gstreamer1.0-plugins-ugly
