### Purpose
This Implementation Guide defines the use of FHIR resources to convey measurements and supporting data from acute care point-of-care medical devices (PoCD) to receiving systems for electronic medical records, clinical decision support, and medical data archiving for aggregate quality measurement and research purposes. It could be considered "deep metadata for device observations". Key goals include supplementing the measurement values with full provenance for traceability, and with further details of device architecture and dynamically changing attributes such as calibration history and battery state than is provided for in a FHIR Observation resource. 

Other related implementation guides focus on home-based personal health devices, and physiological and technical alerts from medical devices.

### Audience
This Implementation Guide is intended for device system developers, system integrators, FHIR architects, and clinical users of point-of-care device information.

### Scope and Boundaries

This Implementation Guide presents data structures and descriptions for the process of mapping point-of-care device logical structure so as to support reporting of observations from such devices and also aspects of dynamic device state and aspects of the provenance of such observations using the conceptual framework and Domain Information Model (IEEE Standard 11073-10201 Medical Device Communications - Domain Information Model.)

Parts of the Domain Information Model that are potential parts of successor Implementation Guides but out of scope for this one include alert (physiological and technical alarms and advisories), and Supervisory Control.

### Relationship to Other Projects & Guides
This Implementation Guide covers material related to work in other projects and guides including the Personal Health Device Implementation Guide, and IHE Patient Care Device (PCD) profiles.

#### Personal Health Device IG
The [Personal Health Device Implementation guide](http://hl7.org/fhir/uv/phd/) treats wellness and chronic disease management devices used mainly by nonprofessionals in home and exercise settings. This Guide is focused on acute-care devices for professional use mainly in healthcare delivery facilities. The Personal Health Device and Point-of-Care Device guides both use information models and nomenclature from the IEEE 11073 Medical Device Communications series of standards and the guides for these two kinds of devices are being developed cooperatively in the Devices On FHIR project with a goal of consistency and ease of use by use by receiving systems.

#### Unique Device Identifier (UDI) IG(s)
This Implementation Guide makes use of Unique Device Identification as defined by the US FDA. Refer to HL7 Cross Paradigm Implementation Guide: UDI Pattern

#### IHE Patient Care Device (PCD) Profiles
The IHE PCD domain has developed profiles for conveying acute care device data with context using HL7 V2. The base information system and nomenclature are based on the IEEE 11073 Medical Device Communications standards, also used in this FHIR Implementation Guide. 

These profiles cover Device Enterprise Communications (DEC), reporting device observations to enterprise systems including near-real-time charting to electronic medical records, clinical decision support systems and patient data archive systems. That is similar to the scope of this FHIR Implementation Guide.

A planned future FHIR use case for the Devices on FHIR group is the near-real-time communication of physiological and technical alerts to clinicians, and internal device status and state transition information for systems designed to process such information. This is similar to IHE PCD Alert Communication Management and Infusion Pump Event Communication profiles.

Other PCD profiles include Implantable Device Cardiac Observations, Point-of-Care Infusion Verification.

#### Vital Signs Profile
The Observation resource is used to record data that is retrieved from a device (see {{pagelink:ObservationProfiles}}).  Some values that are formalized in this resource are required to conform to the [Vital Signs Profile](http://hl7.org/fhir/observation-vitalsigns.html).  For example, heart rate or respiratory rate, many of which are often provided by a PoCD patient-connected device.  

This requirement is a challenge, though, for devices that only communicate ISO/IEEE 11073 terminology (the Vital Signs Profile) requires LOINC and UCUM).  As a result, provisions must be made to correctly make the mapping for these terms from 11073 to LOINC and to ensure that they are done at the earliest possible point.

This is an area of coordination between this IG and the Vital Signs Profile.

### Structure of this Guide

This guide is organized into presentations of an overview of the work, explanations of its use, specializations, and extensions of FHIR resources to meet its design goals.

### Abbreviations & Conventions

* MDC
** Medical Device Communications, the general name for standards in the IEEE 11073 series
* PoCD
** Point-of-Care Device, the category of communications-capable acute-care medical devices, generally intended for use by qualified healthcare professionals and subject to regulatory review
* PHD
** Personal Health Device, the category of communications-capable personal health and wellness devices designed to be used by persons without professional training and not always subject to regulatory review
* X73
** Informal short form often used to refer to the IEEE 11073 suite of standards
* 11073 
** IEEE 11073 Medical Device Communications standards serices
* healthcare devices vs. medical devices
** healthcare devices refers to the broad category of devices used in some way in healthcare. Medical device is defined in regulations and implies use in determining treatment of patients

### Future Guide Revisions
Future capabilities are planned for this General PoCD IG including:
1. Waveform Support
2. Device Events & Alerts including:
  * Basic PCD ACM / 60601-1-8 reporting
  * Status notifications back to the source Device
3. Query for fresh data:
  * Indirect via a FHIR gateway where a request is made to the device using Protocol (X)
  * Direct to the device where it has a minimized server capability
         
