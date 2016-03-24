# hifiberry-player
How to enable Hifiberry on a NOOB distribution

1) Hardware requirements: 
- Raspberry Pi Model B (1-st gen)
- Hifiberry DAC+ (see https://www.hifiberry.com/dacplus/)

2) Install NOOBS distribution:
Follow the instructions from https://www.raspberrypi.org/help/noobs-setup/
It already has Python and JDK installed

3) Configure sound card 
Shorter instruction:
Edit /boot/config.txt
sudo nano /boot/config.txt

comment out line 
dtparam=audio=on

add line
dtoverlay=hifiberry-dacplus

Create /etc/asound.conf with the following content:
pcm.!default  {
 type hw card 0
}
ctl.!default {
 type hw card 0
}

Test it:
pi@raspberrypi ~ $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: sndrpihifiberry [snd_rpi_hifiberry_dac], device 0: HifiBerry DAC HiFi pcm5102a-hifi-0 []
Subdevices: 1/1
Subdevice #0: subdevice #0

Install mplayer
sudo apt-get install mplayer

Enjoy the music:
mplayer http://ice1.somafm.com/secretagent-128-mp3


(longer instruction see here: https://www.hifiberry.com/guides/configuring-linux-3-18-x/)
