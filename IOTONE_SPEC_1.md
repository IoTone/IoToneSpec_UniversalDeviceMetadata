Universal Device Metadata (UDM) Specification draft v0.9
========================================================

This document is released under the terms of the [Apache 2.0 License](https://raw.githubusercontent.com/IoTone/IoToneSpec_UniversalDeviceMetadata/master/LICENSE)

Copyright 2014 IoTone, Inc.

# Abstract

Universal Device Metadata(UDM) Specification is a microformat intended to describe any kind of device and its characteristics.  It isn't intended as a programmatic interface description to low level hardware details (like addresses and registers), but as a high level reference to a device's overall hardware specs, like memory, CPU details, etc. 

# Conformance

 The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in RFC 2119 [RFC2119].

 The terms "JSON", "JSON text", "JSON value", "member", "element", "object", "array", "number", "string", "boolean", "true", "false", and "null" in this document are to be interpreted as defined in RFC 4627 [RFC4627]. 

# Terminology

## JSON Primitives

The following primitves are:

*    array
>        A JSON array. 
*   boolean
>        A JSON boolean. 
*    integer
>        A JSON number without a fraction or exponent part. 
*    number
>        Any JSON number. Number includes integer. 
*    null
>        The JSON null value. 
*    object
>        A JSON object. 
*    string
>        A JSON string. 


# Overview

There are numerous standards and ad-hoc approaches to defining device specifications with varying levels of granularity.  In terms of the nature and rigor of the data captured, some approaches require very strict schema definition, while others are very loose and capable of being extended over time.  As well, the format of the data varies (binary, xml, text, key value properties, json, sql, etc..).  Because of these differences, there isn't a good universal approach on the market, making it possible to get stuck in committee based standards, stove pipe proprietary approaches requiring a license, or incompatible approaches. 

Since there is no approach that fits the requirements, define one.  The proposal is to use a schema-free approach in terms of requiring conformance, putting the burden on the application to perform validation and constraint checks.  It is also proposed to go with a nearly universal format that is easy to deal with.  JSON seems to meet these criteria.  JSON-Schema will be provided to offer enough guidance for anyone to quickly and easily create device specifications.

# Requirements 

-    Simple 
-   Human Readable 
-    Machine Readable 
-    Supports Nested Definitions 
-    Defines the key attributes of any device, essentially, a generic product datasheet definition 
-    NoSQL DB Friendly (i.e. JSON) 
-    Supports linking 
-    No Standards Body necessary 
-    Doesn't duplicate an existing solution that is clearly already good enough 
-    Future proof through extensibility 
-    No 3rd Party Intellectual Property Rights associated with the design
-    Easily handle self-referential attributes

# Common Device Attributes

Below are a list of attributes that will be used to compose UDM.

udm_devices
```
[udm_device*]
```

udm_device
```
{}
{ members }
```

members 
```
Attrpair 
device 
attrpair , device, members 
```

attrpair 
```
descriptiveattrkey : value 
```

value 
```
Any value JSON value 
```
 
descriptiveattrkey 
```
Any valid JSON String 
udm_schema_name
udm_dataset_name
udm_version
udm_key
udm_guid
udm_serialno
udm_class
udm_type
udm_capabilities
udm_model_name
udm_mktg_name
udm_model_number
udm_model_rev
udm_oem 
udm_chipset_details {
   udm_chipset_inst_set
   udm_chipset_vendor 
   udm_chipset_type 
   udm_cpu_max_frequency 
   udm_cpu_number_of_cores 
}
udm_network_interfaces {
   udm_network_interface
}
udm_battery_details
udm_tags 
udm_memory_volatile
udm_memory_non_volatile
udm_hdds
udm_sensors
udm_io_ports
udm_internal_slots
udm_power_input
udm_power_outputs
udm_vendor
udm_mfg_origin
udm_mfg_date
udm_displays
udm_services_link
```

Users of UDM are free to define custom attributes to meet needs not yet forseen.

# UDM Schema

It is recommended to follow the JSON-Schema format to provide conforming schema definitions for the initial specification.  However, JSON-Schema isn't strictly necessary to implement this specification.

The draft schema follows below.  It was generated using a sample input into http://www.jsonschema.net/
```
{
   "type":"object",
   "$schema":"http://json-schema.org/draft-03/schema",
   "id":"http://iotone.org/specs/1/schema",
   "required":false,
   "properties":{
      "udm_schema_name":{
         "type":"string",
         "id":"http://iotone.org/specs/1/schema/udm_schema_name",
         "required":false
      },
      "udm_dataset_name":{
         "type":"string",
         "id":"http://iotone.org/specs/1/schema/udm_dataset_name",
         "required":false
      },
      "udm_version":{
         "type":"string",
         "id":"http://iotone.org/specs/1/schema/udm_version",
         "required":false
      },
      "udm_devices":{
         "type":"array",
         "id":"http://iotone.org/specs/1/schema/udm_devices",
         "required":true,
         "items":{
            "type":"object",
            "id":"http://iotone.org/specs/1/schema/udm_devices/0",
            "required":false,
            "properties":{
               "udm_key":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_key",
                  "required":false
               },
               "udm_guid":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_guid",
                  "required":false
               },
               "udm_schema_name":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_schema_name",
                  "required":false
               },
               "udm_os_version":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_os_version",
                  "required":false
               },
               "udm_os":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_os",
                  "required":false
               },
               "udm_serialno":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_serialno",
                  "required":false
               },
               "udm_class":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_class",
                  "required":false
               },
               "udm_type":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_type",
                  "required":false
               },
               "udm_capabilities":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_capabilities",
                  "required":false
               },
               "udm_model_name":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_model_name",
                  "required":false
               },
               udm_model_rev":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_model_rev",
                  "required":false
               },
               "udm_mktg_name":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_mktg_name",
                  "required":false
               },
               "udm_model_number":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_model_number",
                  "required":false
               },
               "udm_oem":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_oem",
                  "required":false
               },
               "udm_chipset_details":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_chipset_details",
                  "required":false
               },
               "udm_network_interfaces":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_network_interfaces",
                  "required":false
               },
               "udm_battery_details":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_battery_details",
                  "required":false
               },
               "udm_tags":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_tags",
                  "required":false
               },
               "udm_memory_volatile":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_memory_volatile",
                  "required":false
               },
               "udm_memory_nonvolatile":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_memory_nonvolatile",
                  "required":false
               },
               "udm_hdds":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_hdds",
                  "required":false
               },
               "udm_sensors":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_sensors",
                  "required":false
               },
               "udm_io_ports":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_ioports",
                  "required":false
               },
               "udm_internal_slots":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_internal_slots",
                  "required":false
               },
               "udm_power_inputs":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_power_inputs",
                  "required":false
               },
               "udm_power_outputs":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_power_outputs",
                  "required":false
               },
               "udm_vendor":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_vendor",
                  "required":false
               },
               "udm_mfg_origin":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_mfg_origin",
                  "required":false
               },
               "udm_mfg_date":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_mfg_date",
                  "required":false
               },
               "udm_displays":{
                  "type":"string",
                  "id":"http://iotone.org/specs/1/schema/udm_devices/0/udm_displays",
                  "required":false
               },
               "udm_services_link": {
                   "id":"http://iotone.org/specs/2/schema/usm_services",
                       "required": false,
                           "type": "array" ,
                               "items": {
                               }
               }
            }
         }
      }
   }
}
```

# Example Use

*Sample Mobile Handsets/Tablets*

```
{
   "udm_version":"0.9",
   "udm_dataset_name": "sample-android-devices"
   "udm_devices": [
      {
         "udm_key": "user-defined-key",
         "udm_model_name": "Nexus",
         "udm_model_number": "Nexus 7",
         "udm_oem": "ASUS",
         "udm_guid": "0585b8a6",
         "udm_os_version": "4.4.2",
         "udm_os": "Android",
         "udm_type": "tablet",
         "udm_memory_volatile": {
            "size": "1GB"
         },
         "udm_memory_non_volatile": {
            "size": "16GB",
            "type": "flash"
         },
         "udm_chipset_details": {
            "udm_chipset_inst_set": "armeabi-v7a",
            "udm_chipset_vendor": "Qualcomm",
            "udm_chipset_type": "Snapdragon S4Pro",
            "udm_cpu_max_frequency": "1.5 GHz",
            "udm_cpu_number_of_cores": "4"
         },
         "udm_displays": [{
            "display_resolution": "1200x1824",
            "ppi": "323"
         }],
         "udm_network_interfaces": [
            { 
               "lo": 
               [ { "address": "127.0.0.1",
                  "family": "IPv4",
                  "internal": true },
                 { "address": "::1",
                   "family": "IPv6",
                   "internal": true } ]
            }, {
               "wlan0": 
               [ { "address": "10.0.0.105",
                  "family": "IPv4",
                  "internal": false },
                 { "address": "fe80::de85:deff:fe90:4cb9",
                   "family": "IPv6",
                   "internal": false } ] 
            }
         ],
         "udm_sensors": {
            "accelerometer": "1",
            "light": "1",
            "gyroscope": "1",
            "orientation": "1",
            "magnetic": "1",
            "sound": "1"
         },
         "udm_services_link": [{
            "usm_key": "myphone.local",
            "usm_type": "webserver"
         }
         ]
      },
      {
         "udm_key": "user-defined-key2",
         "udm_model_name": "Galaxy S II",
         "udm_model_number": "I9100",
         "udm_oem": "Samsung",
         "udm_guid": "a80000Bf1f002",
         "udm_os_version": "4.0.4",
         "udm_os": "Android",
         "udm_type": "phone",
         "udm_chipset_details": {
            "udm_chipset_inst_set": "armeabi-v7a",
            "udm_chipset_vendor": "Exynos",
            "udm_chipset_type": "4210",
            "udm_cpu_max_frequency": "1.0 GHz",
            "udm_cpu_number_of_cores": "2"
         },
         "udm_displays": [{
            "display_resolution": "480x800",
            "ppi": "217"
         }],
         "udm_network_interfaces": [
            { 
               "lo": 
               [ { "address": "127.0.0.1",
                  "family": "IPv4",
                  "internal": true },
                 { "address": "::1",
                   "family": "IPv6",
                   "internal": true } ]
            }, {
               "wlan0": 
               [ { "address": "10.0.0.3",
                  "family": "IPv4",
                  "internal": false },
                 { "address": "fe80::de85:deff:fe90:4cb8",
                   "family": "IPv6",
                   "internal": false } ] 
            }
         ],
         "udm_sensors": {
            "accelerometer": "1",
            "compass": "1",
            "gyroscope": "1",
            "proximity": "1"
         },
         "udm_io_ports": {
            "USB": "Host/Device",
            "SPI": "2",
            "I2C": "2",
            "UART": "3",
            "PWM": "TPM",
            "ADC": "16 bit",
            "DAC": "1x 12bit",
            "Touch Sensor": "1",
            "GPIO": "66" 
         }
      }
   ]
}
```

*Sample Microcontroller*
```
{
   "udm_version":"0.9",
   "udm_devices": [
      {
         "udm_key": "user-defined-key3",
         "udm_model_name": "FRDM-KL25Z",
         "udm_model_number": "MKL25Z128VLK4",
         "udm_oem": "Freescale",
         "udm_guid": "33u821381203810jdsd01231",
         "udm_os_version": "20140530_k20dx128_kl25z_if_opensda",
         "udm_os": "mbed",
         "udm_type": "32-bit mcu",
         "udm_memory_volatile": {
            "size": "16kB"
         },
         "udm_memory_non_volatile": {
            "size": "128kB",
            "type": "flash"
         },
         "udm_chipset_details": {
            "udm_chipset_inst_set": "arm-thumb",
            "udm_chipset_vendor": "Freescale",
            "udm_chipset_type": "ARM® Cortex™-M0+ Core",
            "udm_cpu_max_frequency": "48 MHz"
         },
         "udm_sensors": {
            "accelerometer": "1",
            "capacative-touch": "1"
         }
      }
   ]
}
```

*Sample Smart Watch*
```
{
   "udm_version":"0.9",
   "udm_devices": [
      {
         "udm_key": "user-defined-key3",
         "udm_model_name": "TOQ",
         "udm_model_number": "ToqSW1",
         "udm_oem": "Qualcomm",
         "udm_guid": "TQ12391js92313132",
         "udm_os": "ThreadX RTOS",
         "udm_type": "smartwatch",
         "udm_memory_volatile": {
            "size": "512MB"
         },
         "udm_memory_non_volatile": {
            "size": "?",
            "type": "flash"
         },
         "udm_chipset_details": {
            "udm_chipset_inst_set": "arm-thumb",
            "udm_chipset_vendor": "Qualcomm",
            "udm_chipset_type": "ARM® Cortex™-M3 Core",
            "udm_cpu_max_frequency": "200 MHz"
         },
         "udm_sensors": {
            "accelerometer": "1",
            "capacative-touch": "1"
         },
         "udm_displays": [{
            "display_resolution": "288X192",
            "size": "1.55in"
         }]
      }
   ]
}
```

*Sample Bluetooth 4.0 Accessory*
```
{
   "udm_version":"0.9",
   "udm_devices": [
      {
         "udm_key": "user-defined-key4",
         "udm_model_name": "SensorTag",
         "udm_model_number": "CC2541DK-MINI",
         "udm_model_rev": "1.0.2",
         "udm_oem": "Texas Instruments",
         "udm_guid": "1293FTI123jf24",
         "udm_type": "ble-accessory",
         "udm_memory_volatile": {
            "size": "8kB"
         },
         "udm_memory_non_volatile": {
            "size": "128kB",
            "type": "flash"
         },
         "udm_chipset_details": {
            "udm_chipset_inst_set": "8051",
            "udm_chipset_vendor": "TI",
            "udm_chipset_type": "CC2540"
         },
         "udm_sensors": {
            "accelerometer": "1",
            "humidity": "1",
            "temperature": "1",
            "pressure": "1",
            "accelerometer": "1",
            "gyroscope": "1",
            "magnetometer": "1",
            "capacative-touch": "1"
         }
      }
   ]
}
```

# Alternatives 

In survey of the possible existing alternatives, there are hints of solutions that come close to what we are looking for.  In most cases, where XML is utilized, the "API Surface" for the definitions becomes vast. 

 

## UPnP 1.1 Device Schema (Appendix B1) 


UPnP 1.1 Device Schema is found in Appendix B1 http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf 

Pro:  

    This is a very well defined specification 

    There are no IP rights associated with the use of the documentation use 
    
    the device specification metadata is quite detailed

Con: 

    XML is fairly heavyweight 

## Certimo.org Device Ratings

The Certimo.org Consortium offers device ratings for Usability.  They provide a very good set of details they collect from
each device.  For example: http://www.certimo.org/devices/samsung-galaxy-s5#node_device_full_group_device_details

This covers all of the essential details for mobile handsets.  It provides many of the details you would expect to see on a 
product datasheet.

Pro:

* Very detailed device profiles for mobile

Con:

* Not distributed in a format that we can consume 
* Mobile handset focused, but doesn't cover details of individual components in great detail


I am still looking for other alternatives. 

# Conclusion 

The UDM solution provides flexibility and some options for a variety of implementation options, by providing guidelines for developers to follow without a heavyweight api or learning curve.  JSON is the easiest format to work with across platforms, without heavy parsing requirements.  It is NoSQL friendly and should be easily implemented. 

# Normative References 

* JSON Spec - http://json.org/ 
*  http://json-schema.org/latest/json-schema-core.html

# Non-Normative References 

* SmartThings Device Type Specification - http://docs.smartthings.com/en/latest/device-type-developers-guide/anatomy-of-a-device-type.html 

* JSON-LD: http://www.w3.org/TR/json-ld-api/ 

*    Nottingham JSON Home: http://tools.ietf.org/html/draft-nottingham-json-home-03 
*    RAML: http://raml.org/index.html 


*    SensorML: http://www.sensorml.com/sensorML-2.0/examples/index.html 

*    Example from ContikiOS, in terms of description of low-level hardware: http://contiki.sourceforge.net/docs/2.6/a00800_source.html  

*    OMA Lightweight M2M: http://technical.openmobilealliance.org/Technical/technical-information/release-program/current-releases/oma-lightweightm2m-v1-0 

*    FI Ware Fi-Lab: http://www.fi-ware.org/tag/raspberry-pi/ 

*    Microformats: http://microformats.org/wiki/Main_Page 

*    DLNA 

*    Certimo Device Specs 

*    GSMArena.com 

*    W3C Mobile Web Initiative Device Descriptor Working Group (DEFUNCT): http://www.w3.org/2005/MWI/DDWG/

*    OMA UAProf Spec (WAP focused): http://openmobilealliance.org/wp-content/uploads/2012/12/wap-248-uaprof-20011020-a.pdf

*    WURF : http://sourceforge.net/projects/wurfl/files/WURFL/

*    Metadata Standards: https://en.wikipedia.org/wiki/Metadata_standards
