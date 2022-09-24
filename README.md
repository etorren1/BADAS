<h1 align="center">
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
<a href="#p2">Part 3: Discovering BGP with EVPN.</a>

## Part 1: GNS3 configuration with Docker <article id="p1"></a>

We must use two images docker. <br>
A first image with a system of your choice. <br>
A second image using a system of your choice with the following constraints:

  • A software that manages packet routing (frr or quagga) <br>
  • The service BGPD active and configured. <br>
  • The service OSPFD active and configured. <br>
  • An IS-IS routing engine service. <br>
  • Busybox or an equivalent.
  
  
  
