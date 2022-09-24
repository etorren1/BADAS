<h1 align="center"> <a name="top"></a>
      Bgp At Doors of Autonomous Systems is Simple
</h1>

<p align="center">
   Always design your network...
</p>

## Introduction

 Project about simulate a network and configure it using GNS3 with images docker <br>
 All configuration files are located in the directories of the same name from the mandatory part

## Mandatory part

<a href="#p1">Part 1: GNS3 configuration with Docker.</a> <br>
<a href="#p2">Part 2: Discovering a VXLAN.</a> <br>
<a href="#p3">Part 3: Discovering BGP with EVPN.</a>

## Part 1: GNS3 configuration with Docker <a name="p1"></a>

We must use two images docker. <br>
A first image with a system of your choice. <br>
A second image using a system of your choice with the following constraints:

  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• A software that manages packet routing (frr or quagga) <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• The service BGPD active and configured. <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• The service OSPFD active and configured. <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• An IS-IS routing engine service. <br>
  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;• Busybox or an equivalent. <br>
  
Below is an example of each image configured in GNS3:  
<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P1/img1.png" width="70%"/></div>
  
##  Part 2: Discovering a VXLAN  <a name="p2"></a>

Now we have a functional basis to start setting up first VXLAN (RFC 7348) network. <br>
First in static then in dynamic multicast. Here is the topology of first VXLAN:

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P2/img7.png" width="50%"/></div>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Configure this network using a VXLAN with an ID of 10 and name vxlan10.  Set up a bridge here: br0.  You must configure your ETHERNET interfaces as you wish. Below is an example of the result when we inspect the traffic between our two machines in our VXLAN:

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P2/img5.png" width="70%"/></div>
<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P2/img6.png" width="70%"/></div>

## Part 3: Discovering BGP with EVPN <a name="p3"></a>

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Now we will explore the principle of the BGP EVPN (rfc 7432) without using MPLS to simplify things. The controller will learn the MAC addresses. We will use our VXLAN with ID 10 seen in the previous part. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;As in the second part we start with the topology of the expected network. We are going to use the principle of the route reflection (=RR). Our leafs (VTEP) will be configured to have dynamic relations. <br>
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;This diagram represents a small datacenter.

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P3/img8.png" width="50%"/></div>

We can see our visibility from our VTEP router_etorren-2 the 3 VTEPs 1.1.1.2

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P3/img9.png" width="70%"/></div>

We have only one route for the moment with our controller (RR) :

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P3/img10.png" width="70%"/></div>

We can see our VNI (10 here) as well as our preconfigured routes (type 3). If host host-3 not running, it route not exist. But we can see type 2 route to host-1 and host-2.

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P3/img11.png" width="70%"/></div>

For our verification a simple ping allows us to see that we can access all the machines through our RR using the VTEPs. We can see the VXLAN configured to 10 as well as our packets ICMP. We also see packets OSPF configured:

<div align="center"><img  src="https://github.com/etorren1/BADASS/blob/master/img/P3/img12.png" width="70%"/></div>

<a href="#top">Gotop</a>
