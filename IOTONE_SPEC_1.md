Universal Device Metadata (UDM) Specification draft v0.9
========================================================

This document is released under the terms of the [Apache 2.0 License](https://raw.githubusercontent.com/IoTone/IoToneSpec_UniversalDeviceMetadata/master/LICENSE)

Copyright 2014 IoTone, Inc.

# Abstract

Universal Device Metadata(UDM) Specification is a microformat intended to describe any kind of device and its characteristics.  It isn't intended as a programmatic interface description to low level hardware details (like addresses and registers), but as a high level reference to a device's overall hardware specs, like memory, CPU details, etc. 

# Problem

There are numerous standards and ad-hoc approaches to defining device specifications with varying levels of granularity.  In terms of the nature and rigor of the data captured, some approaches require very strict schema definition, while others are very loose and capable of being extended over time.  As well, the format of the data varies (binary, xml, text, key value properties, json, sql, etc..).  Because of these differences, there isn't a good universal approach on the market, making it possible to get stuck in committee based standards, stove pipe proprietary approaches, or incompatible approaches. 


# Solution 

Since there is no approach, define one.  We propose a schema-free approach, putting the burden on the application to perform validation and constraint checks.  We also propose to go with a nearly universal format that is easy to deal with.  JSON seems to meet these criteria.  We can use it to provide enough guidance for anyone to quickly and easily create device specifications. 

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

# Implementation 

Define a BNF Grammar for description, so one can easily write a parser, though this is more instructional for potential users than it is for the purposes of needing to write a parser. 

devices
> [[device*]]

device
> blah blah
>   {}
>   { members }

members 
> Attrpair 
> device 
> attrpair , device, members 

attrpair 
> descriptiveattrkey : value 

value 
> Any value JSON value 
 
descriptiveattrkey 
> Any valid JSON String 
> udm_key 
> udm_guid 
> udm_class 
> udm_model_name 
> udm_model_number 
> udm_oem 
> udm_chipset_vendor 
> udm_chipset_type 
> udm_cpu_max_frequency 
> udm_cpu_number_of_cores 
> udm_network_interfaces 
> udm_network_interface [TODO, elaborate on this] 
> udm_tags 
> udm_serialno 
> udm_spec_version

It is recommended to follow the JSON-Schema format to provide conforming schema definitions for the initial specification.  However, JSON-Schema isn't strictly necessary to implement this specification.

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

# Non-Normative References 


* JSON Spec - http://json.org/ 

* SmartThings Device Type Specification - http://docs.smartthings.com/en/latest/device-type-developers-guide/anatomy-of-a-device-type.html 

* JSON-LD: http://www.w3.org/TR/json-ld-api/ 

*    Nottingham JSON Home: http://tools.ietf.org/html/draft-nottingham-json-home-03 
*    RAML: http://raml.org/index.html 

*  JSON Schema: http://json-schema.org/ 

*    SensorML: http://www.sensorml.com/sensorML-2.0/examples/index.html 

*    Example from ContikiOS, in terms of description of low-level hardware: http://contiki.sourceforge.net/docs/2.6/a00800_source.html  

*    OMA Lightweight M2M: http://technical.openmobilealliance.org/Technical/technical-information/release-program/current-releases/oma-lightweightm2m-v1-0 

*    FI Ware Fi-Lab: http://www.fi-ware.org/tag/raspberry-pi/ 

*    Microformats: http://microformats.org/wiki/Main_Page 

*    DLNA 

*    Certimo Device Specs 

*    GSMArena.com 

