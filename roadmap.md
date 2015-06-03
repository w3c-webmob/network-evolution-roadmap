## Mobile Operator Network Current Status and Roadmap for Web & Internet Standards Setters and Developers

### Abstract
This document aims to provide W3C groups and developers with a broad overview of the evolution of the mobile network between 2015 and 2020. This can be used to develop standards that are operator-network-aware ensuring technologies do not clash between the web and the mobile operator network.

### Introduction
Quick overview of the document - aims including "a roadmap of the expected evolution of mobile networks which have potential impacts on Web applications".

### Terminology

* CDMA2000 - 3G mobile technology for sending voice, data, and signaling data between mobile phones and cell sites. It is developed by 3GPP2 and used especially in North America and South Korea.
* CDMA2000 1X - Voice standard of CDMA2000
* CDMA2000 1xEV-DO - Data standard of CDMA2000. Revision A introduced protocols, new forward link data rates and quality of service flags to allow for use cases such as VoIP. Revision B improved the standard by managing edge-of-cell signal, using multiplexing to reduce latency and higher rates satisying use cases such as high definition video streaming.
* GSM - 2G standard developed by the standards body ETSI. It operators in 219 countries as of 2014. It originally had no data requirements, later it expanded to include data communications including GPRS (around 56–114 kbit/s) and EDGE standards (around 400–1000 kbit/s).
* UMTS - 3G mobile telecommunications system developed by 3GPP. UMTS is a circuit plus packet switching combined network. UMTS uses WCDMA.
* WCDMA - 3G mobile technology for voice, text, MMS and data communications. 
* WCDMA HSPA - Data communications which extends WCDMA using shared channel, higher modulation and other methods to increase rates  (around 7–42 Mbit/s). HSPA+ extends these data rates up to 84 Mbit/s. In 2011 HSPA+ was operational in 170 countries. 
* LTE - 4G mobile technology, short for "Long Term Evolution", developed for data communication and maintained by 3GPP. LTE is an all-IP flat architecture system. Users need an LTE capable device to make use of LTE as LTE operates on a separate radio spectrum. 
* TD-LTE - (Time-Division Duplex LTE) one of the two variants of LTE (the other being LTE-FDD). The differences exist between uploading and downloading data. LTE-TDD uses a single frequency, alternating between uploading and downloading data through time.
* LTE-U - LTE for the unlicensed band.
* LTE-eMBMS - LTE Enhanced Multimedia Broadcast Services.  Provides for point-to-multipoint transmission over LTE, and is compatible with HTTP streaming techniques such as DASH (Dynamic Adatpive Streaming over HTTP).
* AXGP - "4G" technology originating in Japan, not LTE but compaitble with TD-LTE systems in China.
* WiMAX
* LTE Advanced - major enhancement to LTE
* TD-LTE Advanced
* WiMAX 2
* iDEN
* TDMA
* Analog

#### Understanding xG
3G, 4G and even 5G are common terms we use to describe networks, but they're not always an accurate representation of "evolution" of the mobile networks. xG terms describe a set of requirements, usually identified by a standards body, which describes what that standards body feels is an acceptable set of requirements for the "next generation" in mobile telecommunications. 4G is a great example: requirements set by the ITU were originally too steep to achieve for the first new hardware tests of LTE, later once the ITU reset the requirements some 3G-based services met the requirements and branded themselves as 4G, despite not being a major system upgrade. (//more explanation please! hardware upgrade? IP network? etc.). To make things clearer mobile operators tend to refer to the technology rather than the xG, most commonly now: LTE.

5G is, however, also often used. This is because no new standard exists for the evolution of the mobile network past LTE currently, therefore only requirements exist under the label "5G". 

#### Downgrading
It is important to understand how devices downgrade. A device will first attempt to register (CORRECT WORD?) a connection with it's highest capable connection mechanism; for most new devices this is LTE. If this is unsuccessul it will downgrade to the next most capable connection (usually HSPA/+) and keep downgrading till it can establish a connection. 

### Current Status (2015)
Mobile operator technologies are heavily standardised, meaning little differentiation between similar level services throughout the globe. However, countries often differ in their deployment of these technologies, resulting in vast differences in throughput and latencies. Most new devices in the developed world will now come LTE enabled, offering 2G, 3G and LTE capabilties although not all developing countries have a widely deployed LTE network (EXAMPLES - spain, uk, us). Furthermore developing countries may offer 3G devices only. (CHECK on 2G only countries, although I think these are gone).

#### LTE
LTE architecture is completely based off of IP. Downlink rates on LTE (rates from the core mobile network to a users device) can reach up to 300 Mbit/s, and latencies in the radio access network can be less than 5ms. LTE deals well with fast moving devices (say, if a user is on a train up to 500km/h depending on frequency band) and supports streaming and multi-casts.

A user will need an LTE-capable device to use LTE. the list of devices which support LTE are constantly growing.  [Wikipedia](http://en.wikipedia.org/wiki/LTE_%28telecommunication%29#Devices) has a good, almost up-to-date list.

Rank	Country/Territory	Penetration
1	 South Korea	62.0%
2	 Japan	21.3%
3	 Australia	21.1%
4	 United States	19.0%
5	 Sweden	14.0%
6	 Canada	8.1%
7	 United Kingdom	5.0%
8	 Germany	3.0%
9	 Russia	2.0%
10	 Philippines	1.0%

__What does this mean for developers?__
???

##### LTE Advanced
As may be obvious by the title LTE Advanced is an enhanced version of LTE. The standards group 3GPP set the standards for LTE Advanced. LTE Advanced uses both the hardware of LTE (so, it is backwards compatible with LTE) but makes changes to elements in the network to meet more strict requirements. LTE Advanced can support up to 100 MHz of aggreated bandwidth (see Carrier Aggregation below), and 3.3Gbit peak download rates in ideal situations. Heterogenous networks (HetNet) are sometimes used to help those users on the edge of the cell (*almost* outside of cell coverage).

A user will need an LTE Advanced-capable device to use LTE Advanced. the list of devices which support LTE are constantly growing.  [Wikipedia][List of devices](http://en.wikipedia.org/wiki/List_of_devices_with_LTE_Advanced).

__What does this mean for developers?__
???

##### LTE eMBMS
eMBMS allows for broadcast services, such as linear television, to be made available over LTE cellular systems.  This allows for broadcast reach to a wide array of mobile devices.  eMBMS is IP compatible, and the 3GPP has standardized the used of Dynamic Adaptive Streaming over HTTP (DASH) for eMBMS.  This allows for HTML5-compatible rendering of eBMBS video services using an off-the-shelf browser provided that the target device is equipped with an eMBMS receiver.
__What does this mean for developers?__
Developers may use HTML5-enabled browsers to develop custom applications that can render broadcast services.
#### 3G Technologies
3G technologies are still the most used generation of ...

__What does this mean for developers?__

How should data be sent, one file, or many different files? How does the network cope with large files?! Etc.

#### 2G

__What does this mean for developers?__

If you are developing an extremely robust application you may need to test your application on the bandwidths your users are likely to experience. Try to find out what the coverage of the mobile network is within the countries / regions you are operating (make sure to check for all of LTE, HSPA, EDGE and GPRS!) and test your app using network restriction tools.

### Current Evolution Areas
Description and impacts of current startegies.

#### Carrier Aggregation
[info](https://www.qualcomm.com/invention/technologies/lte/lte-carrier-aggregation)

Carrier aggregation combines mobile operator networks to offer a larger bitrate to the user. Carrier aggregation used LTE technologies to do this. Up to five operators can currently "aggregate" as per the last set of 3GPP standards. Currently carrier aggregation only works for the "downlink" (traffic flowing from the core operator network to the device), but uplink aggregation will come soon.

Impacts?

#### Network Management
Detail network management and impacts

### Long Term Evolution Areas
Description and impacts of long term startegies.

#### 5G
As of May 2015 there are no defined requirements for 5G which have been agreed by a consensus of mobile network operators. Mobile Network Operators are currently working with a number of standards bodies to define these, and are basing these numbers off predictions of what a 5G network should be able to achieve to account for things such as: video data transfer, WebRTC, increase in web traffic, and internet of things devices. 

[more needed?]

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
