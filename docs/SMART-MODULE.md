# Sensor setup
The pH sensor that I used was from DF Robot. It comes with a decent amount of documentation of its own, but it is meant for Arduino. To set it up with Particle Photon is not very different. To set it up, use electrical wires to connect the sensor in to the Photon using this electrical diagram. The download link for the electrical diagam .fzz file is [here](https://github.com/malikmayank/hydroponic/blob/caitlin/phsensor_photon.fzz).

<img src="pHSensorCloseUp.png" width="1000">
<img src="pHSensor.png" width="1000">

Next, to get readings from the sensor, you will need to run a simple program. Go to the [Particle IDE](https://build.particle.io/build). You will be running the code from my file [pHRead.ino](https://github.com/malikmayank/hydroponic/blob/caitlin/pHRead.ino), which will display the data from the sensor every 5 seconds. When runing this code, take off the cap of the pH sensor and place it in a liquid that you want to measure, such as water.

To callibrate your sensor, you will need to test the readings of multiple different liquids with known pH's, such as water, dish soap, tea, and vinegar. Once you have some data, divide the sensor reading of each liqud by the expected pH for that liquid. Average out these numbers to determine what to divide your sensor reading by. My numbers averaged out to about 350. So, in my final program, I divided the sensor reasings by 350 to get the pH.



# Microcontroller Setup

This [link](https://docs.particle.io/quickstart/photon/) has everything you need to know/do to setup and activate the Particle Photon.


# Slack Integration

The Particle Photon has a lot of great tutoritals for its sensor kit [here](https://docs.particle.io/tutorials/hardware-projects/maker-kit). There is a tutorial there with a video for a conference room monitor that uses slack integrating that is pretty similar to this project.

### Setting up Slack
1. Create the slack channel that you want to post messages in
2. Go to the settings of that channel and choose "add app or integration"
3. Search and select 'incoming webhook'
4. On the next page, choose 'add configuration', and choose the channel you just created
5. Copy your webhook URL, which you will need later.
6. Name your webhook (I used pH Sensor)
7. Save

### Setting up Particle
1. Go to [Particle Console](http://console.particle.io/) integration tab, and create a new integration
2. Choose webhook
3. Name your webhook something like ph_sensor
4. Paste your slack URL that you copied during step 5 above
5. Go to the advanced settings and select 'custom' under JSON data.
6. Add code to display your message, such as:
{
    "text": "The pH is {{PARTICLE_EVENT_VALUE}}."
}
7. Click 'create webhook'

After setting up the Slack integration, you can use the [pH sensor code](https://github.com/malikmayank/hydroponic/blob/master/water-ph.ino) to start getting pH readings on Slack!
