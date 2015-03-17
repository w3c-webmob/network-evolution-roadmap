## Roadmap

### Abstract
This document aims to provide W3C groups and developers with a broad overview of the evolution of the mobile network between 2015 and 2020. This can be used to develop standards that are operator-network-aware ensuring technologies do not clash between the web and the mobile operator network.

### Introduction
Quick overview of the document - aims including "a roadmap of the expected evolution of mobile networks which have potential impacts on Web applications".

### Terminology

* CDMA2000 - 3G mobile technology for sending voice, data, and signaling data between mobile phones and cell sites. It is developed by 3GPP2 and used especially in North America and South Korea.
* CDMA2000 1X - Voice standard of CDMA2000
* CDMA2000 1xEV-DO - Data standard of CDMA2000. Revision A introduced protocols, new forward link data rates and quality of service flags to allow for use cases such as VoIP. Revision B improved the standard by managing edge-of-cell signal, using multiplexing to reduce latency and higher rates satisying use cases such as high definition video streaming.
* GSM - 2G standard developed by the standards body ETSI. It operators in 219 countries as of 2014. It originally had no data requirements, later it expanded to include data communications including GPRS (around 56–114 kbit/s) and EDGE standards (around 400–1000 kbit/s).
* UMTS - 3G mobile telecommunications system developed by 3GPP. UMTS uses WCDMA.
* WCDMA - 3G mobile technology for voice, text, MMS and data communications. 
* WCDMA HSPA - Data communications which extends WCDMA using shared channel, higher modulation and other methods to increase rates  (around 7–42 Mbit/s). HSPA+ extends these data rates up to 84 Mbit/s. In 2011 HSPA+ was operational in 170 countries. 
* LTE - 4G mobile technology, short for "Long Term Evolution", developed for data communication and maintained by 3GPP. Users need an LTE capable device to make use of LTE as LTE operates on a separate radio spectrum. 
* TD-LTE
* AXGP
* WiMAX
* LTE Advanced
* TD-LTE Advanced
* WiMAX 2
* iDEN
* TDMA
* Analog

#### Understanding xG
3G, 4G and even 5G are common terms we use to describe networks, but they're not always an accurate representation of "evolution" of the mobile networks. xG terms describe a set of requirements, usually identified by a standards body, which describes what that standards body feels is an acceptable set of requirements for the "next generation" in mobile telecommunications. 4G is a great example: requirements set by the ITU were originally too steep to achieve for the first new hardware tests of LTE, later once the ITU reset the requirements some 3G-based services met the requirements and branded themselves as 4G, despite not being a major system upgrade. (//more explanation please! hardware upgrade? IP network? etc.). To make things clearer mobile operators tend to refer to the technology rather than the xG, most commonly now: LTE.

5G is, however, also often used. This is because no new standard exists for the evolution of the mobile network past LTE currently, therefore only requirements exist under the label "5G". 

### Current Status (2015)
Overview of expectations for 2015 including:
* countries / subscribers on 3G
* countries / subscribers on LTE
* Notable smaller updates

Mobile operator technologies are heavily standardised, meaning little differentiation between similar level services throughout the globe. However, countries often differ in their deployment of these technologies, resulting in vast differences in throughput and latencies. Most new devices in the developed world will now come LTE enabled, offering 2G, 3G and LTE capabilties although not all developing countries have a widely deployed LTE network (EXAMPLES - spain, uk, us). Furthermore developing countries may offer 3G devices only. (CHECK on 2G only countries, although I think these are gone).

#### Downgrading
It is important to understand how devices downgrade. A device will first attempt to register (CORRECT WORD?) a connection with it's highest capable connection mechanism; for most new devices this is LTE. If this is unsuccessul it will downgrade to the next most capable connection (usually HSPA/+) and keep downgrading till it can establish a connection. 


__What does this mean for developers?__

If you are developing an extremely robust application you may need to test your application on the bandwidths your users are likely to experience. Try to find out what the coverage of the mobile network is within the countries / regions you are operating (make sure to check for all of LTE, HSPA, EDGE and GPRS!) and test your app using network restriction tools.

### Current Evolution Areas
Description and impacts of current startegies.

#### Carrier Aggregation
Detail carrier aggregation and impacts

#### Network Management
Detail network management and impacts

### Long Term Evolution Areas
Description and impacts of long term startegies.

#### 5G
Detail 5G and impacts

#### NFV
Detail Network functions virtualization and impacts

#### SDN
Software Defined Networking

#### MEC
Detail Mobile Edge Computing and impacts
[MEC at ETSI](https://portal.etsi.org/Portals/0/TBpages/MEC/Docs/Mobile-edge_Computing_-_Introductory_Technical_White_Paper_V1%2018-09-14.pdf)

### Tools
network restriction tools
* AT&T Aro
* Chrome Devkit

### Conclusion
Erm, we need to write a conclusion, right?
