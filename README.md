ESP-IDF template app
====================

This is a template application to be used with [Espressif IoT Development Framework](https://github.com/espressif/esp-idf).

Please check [ESP-IDF docs](https://docs.espressif.com/projects/esp-idf/en/latest/get-started/index.html) for getting started instructions.

*Code in this repository is in the Public Domain (or CC0 licensed, at your option.)
Unless required by applicable law or agreed to in writing, this
software is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied.*

Author : Manojkumar 

# Notes for starting new ESP32 Projects

 ## How to add own C source file to compile during ```make``` ?

 - ```mkdir``` **components** in ```project_directory```  and put all the C source files.
 
 -  ```touch``` **component.mk** inside the  **components** directory<b>,</b>  **component.mk** contains info on what files to include during ```make```

 Example snippet of component.mk below :

 ```
#
# Main Makefile. This is basically the same as a component makefile.
#
# (Uses default behaviour of compiling all source files in directory, adding 'include' to include path.)

COMPONENT_SRCDIRS := . 
COMPONENT_ADD_INCLUDEDIRS := .
 ```
 
The tree look of the directory **components** with the source  and it's header files
```
components/
├── component.mk
├── esp_mesh.h
├── mesh_light.h
└── mesh_main.c
```


## How to add modules of large library to compile during ```make flash``` ?
- The sources are inside a each folder containing all the depedent C codes and headers

The tree look of the directory **components** with the source  and it's header files

```
components/
│
├── spidriver
│   ├── component.mk
│   ├── spi_master_lobo.c
│   └── spi_master_lobo.h
├── spiffs
│   ├── component.mk
│   └── esp_spiffs.c
└── tft
    ├── component.mk
    ├── tftspi.c
    └── tftspi.c
```