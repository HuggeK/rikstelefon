![alt text](pictures/IMG_8168.JPEG)

# rikstelefon
A small project for using the libary Pulse Count Controller (PCNT) from ESP-IDF on a ESP32-C6 board to decode the dial on a an old BC 310(Televerkets catalogue), the model is from 1924, when the first automatic switch was introduced (Norra Vasa).


## Background:

This project started when my family bought an old BC 310 telephone on an auction back in Spring 2023. I have then cleaned the Telephone and tried to identify the model of this particular Eriksson RIKSTELEFON. Thanks to the kind people in the Facebook Group [STSF - Telehistoria](https://www.facebook.com/groups/146508645530424/) we where able to determine the Model of it. Link to the post: https://www.facebook.com/groups/146508645530424/permalink/2954014218113172/


# Explanation of the repository structure:

'\src' contains the code for using the PCNT library to decode the method, the ESP-IDF project.

## How to run:

Setup ESP-IDF 6.0. I used , do not forget to set the PATH variables for the ESP IDF and tools. Also set the targeted board, I used a ESP32C6 but it should work on other models too.
Then build by running in the ESP-IDF shell: `idf.py build` and then flash it to the connected ESP32C6 by running `idf.py -p PORT flash` where PORT is the port of the connected ESP32 by UART. You can also monitor the output by running `idf.py -p PORT monitor`.

## TODO:

- [ ] Basic read of the pulses, sending it out on UART when the number dialed have been determined.
- [ ] Thread configuration with support of providing credentials in `main\Kconfig.projbuild`.
- [ ] Matter support.


## Pictures of the telephone:

### Overview:

<!-- <img src="image.png" width="200" height="100"> -->

![alt text](pictures/IMG_8234.JPEG)
![alt text](pictures/IMG_8235.JPEG)
![alt text](pictures/IMG_8237.JPEG)
![alt text](pictures/IMG_8137.JPEG)
![alt text](pictures/IMG_8238.JPEG)
![alt text](pictures/IMG_8232.JPEG)
![alt text](pictures/IMG_8233.JPEG)
![alt text](pictures/IMG_8175.JPEG)
![alt text](pictures/IMG_8237-1.JPEG)
![alt text](pictures/IMG_8136.JPEG)
![alt text](pictures/IMG_8162.JPEG)
![alt text](pictures/IMG_8161.JPEG)

![alt text](pictures/IMG_8160.JPEG)


### Internal terminationsm on both side of "block"
![alt text](pictures/IMG_8144.JPEG)
![alt text](pictures/IMG_8165.JPEG)
![alt text](pictures/IMG_8180.JPEG)
![alt text](pictures/IMG_8184.JPEG)
![alt text](pictures/IMG_8201.JPEG)
![alt text](pictures/IMG_8192.JPEG)
![alt text](pictures/IMG_8202.JPEG)
![alt text](pictures/IMG_8197.JPEG)
![alt text](pictures/IMG_8186.JPEG)


### "Short-button" and hook/body?
![alt text](pictures/IMG_8176.JPEG)
![alt text](pictures/IMG_8194.JPEG)


### Dial internal:
![alt text](pictures/IMG_8206.JPEG)
![alt text](pictures/IMG_8214.JPEG)


### Testing:
![alt text](pictures/IMG_8218.JPEG)
![alt text](pictures/IMG_8145.JPEG)

See videos in '\videos' for a multimeter read of the continuity connected on some test points when the dial is dialed.
<video controls src="videos/IMG_8221.MP4" title="Title"></video>

## Hundred year old capacitors and other internal contactors/pictures:
![alt text](pictures/IMG_8152.JPEG)
![alt text](pictures/IMG_8148.JPEG)
![alt text](pictures/IMG_8153.JPEG)
![alt text](pictures/IMG_8187.JPEG)
![alt text](pictures/IMG_8156.JPEG)
![alt text](pictures/IMG_8198.JPEG)
![alt text](pictures/IMG_8147.JPEG)
![alt text](pictures/IMG_8146.JPEG)
![alt text](pictures/IMG_8150.JPEG)

## Wiring diagrams curtesy of Hans Kårholm:

![Schemor telefonapparater och växlar](pictures/catalogue/494711712_10229955705337404_3239949687065686063_n.jpg)
![BC 310](pictures/catalogue/494711712_10229955705337404_3239949687065686063_n.jpg)
![BC 310](pictures/catalogue/495057579_10229955706177425_5760641331445916385_n.jpg)

## Goal

My first goal is to use the PCNT libary which is provided by ESP-IDF to decode the dials signal and the output a number over serial. In the future it would be cool to make a Matter Thread device and join this into my fabric to be able to trigger automations based on the number dialed.



## References:

### The old telephone itself:
- [1] https://www.hjordis.se/jla/tfn/app/bc310/index.html 
- [2] https://digitaltmuseum.se/021026308218/telefonapparat
- [3] https://sv.wikipedia.org/wiki/Nummerskiva

### Seting up ESP-IDF:
- https://docs.espressif.com/projects/esp-idf/en/v6.0/esp32c6/get-started/index.html
- https://docs.espressif.com/projects/esp-idf/en/v6.0/esp32c6/get-started/windows-start-project.html
- https://docs.espressif.com/projects/esp-idf/en/v6.0/esp32c6/api-guides/build-system.html#idf-py
- 

### Esp32 Pulse Count Controller (PCNT):
- https://docs.espressif.com/projects/esp-idf/en/v6.0/esp32c6/api-reference/peripherals/pcnt.html
- https://documentation.espressif.com/esp32-c6_technical_reference_manual_en.pdf#pcnt
- https://github.com/espressif/esp-idf/blob/release/v6.0/components/esp_driver_pcnt/include/driver/pulse_cnt.h
- https://github.com/espressif/esp-idf/tree/cc5440f/examples/peripherals/pcnt

### Matter Device using OpenThread:
- https://docs.espressif.com/projects/esp-matter/en/latest/esp32/
- https://docs.espressif.com/projects/esp-idf/en/v6.0/esp32c6/api-guides/openthread.html
- 


## BOM:

- BC 310 or any other old telephone with a dial which sends pulses.
- [Esp32-C6](https://www.electrokit.com/utvecklingskort-esp32-c6)
- Dupont cables for development and some 


## lessons learned 

I started this project by cleaning the insides of the telephone to remove all the dust that had built up since it was made.

I then soldering the pin headers to the ESP32-C6-Zero card from waveshare I bought on Electrokit. You can also buy pre-soldered headers. I then used a multimeter to map out where everything was connected to, see pictures with the first attempt to draw some numbers on the pictures. When I google I found [1] which outlined that the button was there to short the microphone when user where listening to get better audio which was an intresting lesson!

When researching this project I came to the realization that in sweden dials was different to the rest of the world, where the number 0 was first (from drawing the finger from) and 9 last in comparision to the rest of the world where it was the other way around[3].

When picking up this project on the 20 of March in 2026 I saw that 10 minutes prior Espressif launched their ESP-IDF suite of tools in version 6.0. [Link to the blog post about their new launch](https://developer.espressif.com/blog/2026/03/idf-v6-0-release/#breaking-changes-know-before-you-upgrade) I then decided to try to use this becuase the blog post mentioned Legacy drivers removed: which the PCNT library I had found was mentioned. My hope is that using the new version I can make my entire home network running on WPA3 only for once.



### License: 

All code, text and pictures is licensed under a CC-BY-4-SA license. 