## Mobile Operator Network Current Status and Roadmap for Web & Internet Standards Setters and Developers

### Abstract
This document aims to provide W3C groups and developers with a broad overview of the evolution of the mobile network between 2015 and 2020. This can be used to develop standards that are operator-network-aware ensuring technologies do not clash between the web and the mobile operator network.

### Introduction
Quick overview of the document - aims including "a roadmap of the expected evolution of mobile networks which have potential impacts on Web applications".

### Mobile Operator Network in a Nutshell
Mobile operator networks are nicely divided into two main sections:

* Radio Access Network (RAN) - connects a user's device to the Core Network. This includes base station which are often grouped in "tracking areas". A Radio Resource Controller lives within the base station and manages the scheduling of who talks when, allocated bandwidth, the signal power used, the power state of each device, and a dozen other variables.
* Core Network - the Core Network connects the radio network to the interent and manages other functions inbetween including routing traffic and billing. The Core Network receives data from the internet into the PGW (Packet Gateway). The PGW manages any policy and billing and passes the data to the SGW (Serving Gateway) to send to the user. The SGW likely does not know where the user is, so queries the MME (Mobility Management Entity) to tell it which base station and location to send the data to to reach the user.

The external network (internet) is connected to the mobile network via the PGW in the core network. The mobile network responsbility ends here. 

#### Understanding xG
3G, 4G and even 5G are common terms we use to describe networks, but they're not always an accurate representation of "evolution" of the mobile networks. xG terms describe a set of requirements, usually identified by a standards body, which describes what that standards body feels is an acceptable set of requirements for the "next generation" in mobile telecommunications. 4G is a great example: requirements set by the ITU were originally too steep to achieve for the first new hardware tests of LTE, later once the ITU reset the requirements some 3G-based services met the requirements and branded themselves as 4G, despite not being a major system upgrade. A major system upgrade in mobile networks would usually require a large hardware change (or rollout) with limited or no backwards compatibility; for LTE the change meant moving to a full IP network, for 5G it may mean virtualisation of the network. 

To make labelling clearer mobile operators tend to refer to the technology rather than the xG, most commonly now: LTE. Since only requirements but no new standards exist for the evolution of the mobile network past LTE, the term "5G" is currently used across users and mobile operators.

#### Downgrading
It is important to understand how devices downgrade. A device will first attempt to setup a connection with it's highest capable connection mechanism; for most new devices this is LTE. If this is unsuccessul it will downgrade to the next most capable connection (usually HSPA/+) and keep downgrading till it can establish a connection. Most devices will report "no connection" if the allowed bandwidth on the connection is less than 100kb/s. 

### Current Status (2015)
Mobile operator technologies are heavily standardised, meaning little differentiation between similar level services throughout the world. However, countries often differ in their deployment of these technologies, resulting in vast differences in throughput and latencies. Most new devices in the developed world will now come LTE enabled, offering 2G, 3G and LTE capabilties. Developing countries may offer 3G devices only, some countries in Africa run 2G networks only, but thankfully these are being upgraded currently.

#### LTE
LTE architecture is a complete IP network (both the Core Network and the RAN use IP). Downlink rates on LTE (rates from the core mobile network to a users device) can reach up to 300 Mbit/s, and latencies in the radio access network (RAN) can be less than 5ms. LTE deals well with fast moving devices (say, if a user is on a train up to 500km/h depending on frequency band) and supports streaming and multi-casts.

A user will need an LTE-capable device to use LTE. the list of devices which support LTE are constantly growing.  [Wikipedia](http://en.wikipedia.org/wiki/LTE_%28telecommunication%29#Devices) has a good, almost up-to-date list.

##### LTE Advanced
As may be obvious by the title LTE Advanced is an enhanced version of LTE. The standards group 3GPP set the standards for LTE Advanced. LTE Advanced uses both the hardware of LTE (so, it is backwards compatible with LTE) but makes changes to elements in the network to meet more strict requirements. LTE Advanced can support up to 100 MHz of aggreated bandwidth (see Carrier Aggregation below), and 3.3Gbit peak download rates in ideal situations. Heterogenous networks (HetNet) are sometimes used to help those users on the edge of the cell (*almost* outside of cell coverage).

A user will need an LTE Advanced-capable device to use LTE Advanced. the list of devices which support LTE are constantly growing.  [Wikipedia][List of devices](http://en.wikipedia.org/wiki/List_of_devices_with_LTE_Advanced).

##### LTE eMBMS
eMBMS allows for broadcast services, such as linear television, to be made available over LTE cellular systems.  This allows for broadcast reach to a wide array of mobile devices.  eMBMS is IP compatible, and the 3GPP has standardized the used of Dynamic Adaptive Streaming over HTTP (DASH) for eMBMS.  This allows for HTML5-compatible rendering of eBMBS video services using an off-the-shelf browser provided that the target device is equipped with an eMBMS receiver.

__What does this mean for developers?__
A request/response round trip on an LTE network will take around 50-100ms. A number of request/responses will need to occur before a user will see the requested web content including: DNS lookup, TCP setup and HTTP connection establishment. If your site runs HTTPS the SSL/TLS handshake must also occur. Some developers aim to achieve the less than 1 second page load time. This is possible with LTE although it is prudent to factor in the number of round trips and the latencies attached to these. Developers can assume then that an LTE connection to an HTTPS site will take around 250ms. After this resources need to be fetched and rendered. 

LTE's bandwidth and speed cabailities allow developers to serve a variety of content in their web apps including HTML5 video, complex images and larger scripts although smaller and fewer resources is always better for performance!

#### 3G Technologies
3G technologies are still the most used generation of ...

__What does this mean for developers?__

How should data be sent, one file, or many different files? How does the network cope with large files?! Etc.

#### 2G
2G networks were first launched in 1991 and although mobile networks have evolved drastically since then 2G is still used in many parts of the world. Data on the original 2G was limited to SMS (text) and MMS (media) messaging. 2.5G (GPRS) added packet switching allowing connections to the internet. 2.75G (EDGE) added new modulation techniques to improve data transmission rates.

2G currently has the largest reach around the world: GSM (a TDMA based 2G technology) reaches 80% of the world's mobile network subscribers and cdmaOne (CDMA based) reaches 17%. However, a number of mobile network operators are beginning to switch their [2G service off](https://en.wikipedia.org/wiki/2G#2G_Shut_Down).

__What does this mean for developers?__
2G networks usually have around around 150 - 400 kb/s of bandwidth. This means serving complex webpages, apps and resources become near impossible. 2G is still widely used around the world, more devices and more people have access to this service than any other. However, developers should remember that some 2G services will be switched off in 2016.

If you want to support 2G you will need to serve as few resources as possible, and make these resources small. Heavy resources such as video or high resolution images won't load over 2G. Developers are still encouraged to load their mobile site over 2G connections but setup some checks to deal with 2G. For instance: make sure your site runs without javascript and still renders nicely in the instance where images might not load. Try to use web fonts where possible (or fall back to a web font which loads nicely on the page) and use image placeholders when images are imperitive to the design. Other normal performance measures should be taken: minimise scripts, use CDNs and allow caching. 

### HTTP and Mobile Networks
The new version of the HTTP protocol (HTTP/2.0) was recently standardised by the IETF. HTTP/2.0 has some impacts to developer performance methods. Pervious performance measures stated that reducing the number of scripts (by creating one large file with all scripts) was better for performance; this was because HTTP/1.1 did not use mutliplexing and had to rely on multiple TCP streams to make multiple requests. HTTP/2.0 uses multiplexing and so can easily make many requests / responses on the same TCP connection. In this case smaller and more scripts and css files are acceptable. 

Mobile networks manages lower layers of communication than HTTP and TCP. Both HTTP and TCP run ''over'' mobile networks so the behaviour of both of these protocols does not impact the behaviour of the mobile network. Developers can then be assured that whether they send one large script file or lots of smaller ones makes a difference to these layers (applicaton and transport) but not to the mobile network.

Although, developers should always be aware that the mobile network behaviour will affect the user experience of their apps and sites, and so should use performance methods to make sure their site copes under any circumstances.

[NETWORK LAYER DIAGRAM]

### Geographical Differences

If you are developing an extremely robust application you may need to test your application on the bandwidths your users are likely to experience. Try to find out what the coverage of the mobile network is within the countries / regions you are operating (make sure to check for all of LTE, HSPA, EDGE and GPRS!) and test your app using network restriction tools.

### Current Evolution Areas
Some mobile operators have been working on and deploying technologies to help improve performance on their networks. Some of these are detailed below. 

#### Carrier Aggregation
Carrier aggregation combines mobile operator LTE networks to offer a larger bitrate to the user. Up to five operators can currently "aggregate" as per the last set of 3GPP standards. Currently carrier aggregation only works for the "downlink" (traffic flowing from the core operator network to the device), but uplink aggregation will come soon.

__What does this mean for developers?__
Countries which have mobile operators using Carrier Aggregation may mean better content delivery and performance. Developers need not do anything to benefit from this. Some developers who robustly test performance may find LTE networks faster and slower across different countries and regions, this will be due to a number of factors and one of those could be Carrier Aggregation. 

#### Transparent Caching
The mobile network's core network often houses transparent caches. These caches exist to allow faster content delivery to users who have visited or accessed this content before. By caching these within the mobile network mobile operators save money by not sending requests to the external internet and users benefit from faster content delivery. More information can be found below in ["Caching and CDNs"](#).

__What does this mean for developers?__
Caching in the mobile network is transparent: this means users and developers have no control over it including controlling how it works or whether they opt in to use it. Some developers have expressed dissatisfaction when mobile netorks have cached resources as it can delay website updates (as cached copies haven't been replaced) or cause irratic behaviour in site loads. The easiest way for developers to prevent any transparent caches from caching their content is to deploy HTTPS; HTTPS content cannot be cached in transparent caches today. Some developers may see performance benefits with transparent caching and may decide to use it through leaving their site as HTTP only, however, there are other strong reasons for moving to HTTPS not discussed in this paper. 

### Long Term Evolution Areas
Description and impacts of long term startegies.

#### 5G
[NGMN](#)(Next Generation Mobile Networks) published 5G requirements as 
[white paper](https://www.ngmn.org/uploads/media/NGMN_5G_White_Paper_V1_0.pdf). 
5G is positioned to address the demands and business contexts of 2020 and beyond. 
It is expected to enable a fully mobile and connected service and to empower 
socio-economic transformations in countless ways many of which are unimagined today, 
including those for productivity, sustainability and well-being. In 5G, NGMN anticipates the need for new radio interface(s) driven by use of higher frequencies, specific use cases such as Internet of Things (IoT) or specific capabilities (e.g., lower latency), which goes beyond what 4G and its enhancements can support.

Now, 3GPP SA1 is dicussing about the service usecase in 5G. The name of study item is Smarter (New Services and Markets Technology Enablers). [info](http://www.3gpp.org/DynaReport/22891.htm)

#### Caching and CDNs
Mobile networks operators use caches and CDNs. The difference is:

* Caching happens without the knowledge of the content provider or user, and they don't need to do anything to make it happen.
* CDNs cache content with the content providers knowledge and consent, usually by signing a contract with a CDN provider (Akamai, CloudFlare etc.).

In the mobile network the largest latencies happen between the operator's Core Network and the device. This is becuase locating users, authenticating their devices and sending the content through the air can take time. Even so, most if the time caching in the mobile operator network happens in the Core Network, this is because not sending requests out to the internet saves operators a lot of money, which hopefully means either more savings for customers or more money put in to update and evolve networks. Also, caching in the RAN is hard; users move often so it is hard to know where to send their cached data, and the number of base stations means caching equipment can become expensive. This may change with [Mobile Edge Computing](#). 

These caches are "transparent" but they will not cache HTTPS data and will respect cache headers. 

Within the next few years we should see a shift away from caching towards CDNs, interconnected CDNs and software defined networking. These new methods of getting content closer to the user may mean a decrease in relianceon normal Core Network caching described here.

#### Network Function Virtualisation (NFV)
NFV is the virtualisation of network function (e.g., MME, SGW, and PGW). Currently mobile networks are built on a lot of physical switches, routers, servers and gateways. NFV wants to change this to virtualised functions, using virtual machines and cloud computing technologies. Thank to NFV, operators can utilize the same physical servers for the different network functions, and reduces the expenditure. This also could mean that operators could expand their networks cheaply and for limited times, so situations such as large events which usually put operator networks under a lot of strain can be handled.  

NFV is usually talked about alongside Software Defined Networking (SDN). NFV and SDN aren't the same thing, and SDN is often used so as to realize the nework where NFV is applied. SDN was defined by some organisations and universities, NFV is developed mainly by service providers including mobile operators. 

#### Mobile Edge Computing (MEC)
In the ["Caching and CDNs"](#) section we explained caching in mobile networks happens mostly in the Core Network. Mobile Edge Computing is a set of new work happening in the ETSI standards body which aims to place intelligent servcer in the RAN. This server will use cloud technologies to manage caches and other intelligent applications like caches or transcoders ultimately allowing content to live or be cached closer to the user saving on the great latencies in mobile networks, or cutting down the time for round trips.

__What does this mean for developers?__
The details of MEC are not decided yet but the ultimate goal is to decrease the latencies for users and take stress off bottlenecks in the operator network. Developers could benefit from a few different ways. First of all content can be placed closer to the user reducing latency times to your site; this could be done transparently, but with end-to-end encryption becoming more wide spread it is more likely developers will need to sign up with a CDN or MEC provider who can provide MEC server caching. Some developers will also have location-specific apps which could sit closer to users in those locations, such as for a large event. Some developers could also push app updates to these MEC servers when they have a large app updates occur. Until MEC is deployed (which won't be until 2017 at the earliest) developers need not do anything apart from submit any relevant use cases to the standards body ETSI. 

[MEC at ETSI](https://portal.etsi.org/Portals/0/TBpages/MEC/Docs/Mobile-edge_Computing_-_Introductory_Technical_White_Paper_V1%2018-09-14.pdf)

### Standards Bodies
It may be helpful to web and internet standards setters and developers to understand the standards bodies in mobile networking and how they interact. A list below introduces these bodies:

* __European Telecommunications Standards Institute (ETSI):__ makes standards for for Information and Communications Technologies (ICT) with a global focus. ETSI organise their standards into technology clusters; relevant to mobile networks includes: security inclyding cyber secuirty, lawful intercept and emergency telecommunication, wireless systems including the standards EDGE, GPRS, UMTS, Mobile Edge Computing and smart cards and standards for Internet of Things including RFID, data security and management and Machine-to-Machine. ETSI has a global focus and is headquartered in Sophia-Antipolis, France.
* __3rd Generation Partnership Project (3GPP):__ a global collaboration between telecommunications associations. Originally 3GPP worked on developing the 3G standard. It now looks after standards for radio access networks (RAN), the core transport network, service capabilities, codecs, security and quality of service. 
* __Open Mobile Alliance (OMA)__: develops standards usually on the application layer for the mobile phone industry. Previously these standards where being worked on in a number of other groups and forums, so the OMA brought them together under the same umbrella. The OMA currently work on standards for Network APIs covering chat, file transfer, image share and messaaging. They also standardise authorisation, secuirty and implementation of Network APIs, provisioning, charging and device management scheduling.
* __GSMA__: The GSMA represents the interests of mobile operators worldwide including running technical projects and policy support. GSMA runs a number of working groups which focus on standards for billing, roaming, security algorithms, terminal testings and building and manitaing the IMEI database. GSMA has a global membership and is headqaurtered in London. 
* __International Telecommunication Union (ITU):__ is an agency of the United Nations which is responsible for issues related to information and communication technologies. Particularly of importance to mobile operators is the ITU manages the global use of radio spectrum and assisting in the development of telecommunicatio standards including data, voice, and next generation networks. In the developing world the ITU works to improve the telecommunication infrastructure. and assists in the development and coordination of worldwide technical standards.

### Tools
network restriction tools
* AT&T Aro
* Chrome Devkit
* facebook tools

### Final Statements
Erm, we need to write a conclusion, right?

### Glossary

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
* NGMN -  mobile telecommunications association of mobile operators, vendors, manufacturers and research institutes. It was founded by major mobile operators in 2006 as an open forum to evaluate candidate technologies to develop a common view of solutions for the next evolution of wireless networks. Its objective is to ensure the successful commercial launch of future mobile broadband networks through a roadmap for technology and friendly user trials. https://www.ngmn.org/
