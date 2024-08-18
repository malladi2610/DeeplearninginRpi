
# Deep Learning in RPi

## Hardware Used
- **Rpi 4B** - 2GB RAM
- **64GB memory card**
- **Pi cam** 10MP

## Software
- **Rpi version 3.5.0**

## Getting Started with RPi

### Software Installation - Raspbian OS
First, the Raspbian OS needs to be burned onto a memory card (minimum 16 GB). Follow these steps:

1. Install the Noobs software using this [link](https://www.raspberrypi.org/downloads/noobs/). You can download it as Torrent or Zip.
2. Extract the zip file to a folder - `RpiOS`.
3. Take a memory card in a card reader and open a software known as [Balena Etcher](https://www.balena.io/etcher/). You can download the software from here.
4. Follow [this video](https://youtu.be/OLJ4E0UWcUo) for assistance in the above process.

### Setting Up the RPi

1. Once the previous step is done, place the memory card into the SD card slot of the RPi, attach a monitor and keyboard to it (required only for the initial setup), and then connect the power supply.
   - Watch [this video](https://youtu.be/y45hsd2AOpw) from 5:50 mins.

2. If you don’t have a monitor and keyboard, then follow these steps for a headless setup:
   - Watch [this video](https://youtu.be/gOLnIrqmPQc) fully to set up in Headless mode.

In this way, the RPi will be ready for your new creations!

## Installing Software for Deep Learning in RPi

### TensorFlow Lite
Here we are going to set up TensorFlow Lite in a virtual environment and test it with Google’s sample model. 

- Watch [this video](https://youtu.be/aimSGOAUI8Y) for reference.

Follow these commands:

```bash
sudo apt-get update
sudo apt-get upgrade
```

- If you are using Pi-cam, then enable it using the preferences tab and reboot it once it is enabled.

```bash
git clone https://github.com/EdjeElectronics/TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi
mv TensorFlow-Lite-Object-Detection-on-Android-and-Raspberry-Pi/ tflite1
cd tflite1
sudo pip3 install virtualenv
python3 -m venv tflite1-env
source tflite1-env/bin/activate
bash get_pi_requirements.sh  # It contains all the required installation
wget https://tfhub.dev/tensorflow/lite-model/ssd_mobilenet_v1/1/metadata/1?lite-format=tflite
unzip coco<press tab-key> -d Sample_TFLite_model
python3 TFLite_detection_webcam.py --modeldir=Sample_TFLite_model
```

- Now, to see the output, either you need to connect your RPi to the monitor or you can use [VNC](https://youtu.be/gCbGmAFqLoU). 
- For SSH or VNC to work, your RPi and the system through which you are accessing it should be connected to the same WiFi network.
- If any error is faced like “cannot currently show the desktop,” refer to [this link](https://www.tomshardware.com/how-to/fix-cannot-currently-show-desktop-error-raspberry-pi).

On running it, a window will open which shows the output of the objects detected by the camera.

In this way, the object detection is done.

An FPS of 4.42 is achieved, which can be drastically increased by using any accelerator like Intel Neural Stick or Google Coral USB accelerator.

In this process, OpenCV is installed but it is not accessible globally. To use OpenCV globally, it needs to be installed as follows:

### OpenCV
Follow the instructions from this video and blog to get it set up:

- [This is the video link](https://youtu.be/ylnjXbcNLJU).
- [This is the blog link](https://www.youtube.com/redirect?event=video_description&v=ylnjXbcNLJU&redir_token=QUFFLUhqbkNFamd6V3loc3llTW9CbmpnTW15UnRCR3hhd3xBQ3Jtc0trdkxGdUdIQVpJbzAtbjRVelJXYWFLa3Rtd2FQaUtsdmRvMnRBV3hPanNqc2dzbTdhb1I3Z0RYQXNFREg0S2MtcHY5V0JiNmd4Y1R2VkhpTnJRNTd0NlpIWk40eVFNRTVrRlRVcGdLbmQ5SDRfelFKUQ%3D%3D&q=https%3A%2F%2Fmedium.com%2F%40aadeshshah%2Fpre-installed-and-pre-configured-raspbian-with-opencv-4-1-0-for-raspberry-pi-3-model-b-b-9c307b9a993a).



