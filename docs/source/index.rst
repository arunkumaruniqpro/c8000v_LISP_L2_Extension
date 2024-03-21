Extending Layer2 across Datacenters using Locator Identity Separation Protocol (LISP)'s!
========================================================================================

The Locator Identity Separation Protocol (LISP) is a new routing architecture that creates a new paradigm by splitting the device identity, known as an Endpoint Identifier (EID), and its location, known as its Routing Locator (RLOC), into two different numbering spaces. This capability brings renewed scale and flexibility to the network in a single protocol, enabling the areas of mobility, scalability and security. 

.. image:: network_diagram.png
  :width: 800
  :alt: Alternative text

In this architecture, there is clear separation between "who" the endpoint is, and "where" the endpoint currently is located. By separating EIDs and RLOCs, LISP inherently enables numerous benefits within a single protocol, including:

Low OpEx multihoming with ingress traffic engineering
Address familiy independence for efficient IPv6 Transition support
High-scale Virtualization/Multi-tenancy support
Data Center/Cloud Mobility support, including session persistence across mobility events
and seamless mobile node support.

Components Involved 
===================

EID (Endpoint Identifier) - IP address of a host
RLOC (Routing Locator) - IP address of the LISP router facing ISP

ITR (Ingress Tunnel Router) -  Sends map requests and processes received map replies in order to resolve EID-to-RLOC mappings. On the data plane side, an ITR receives packets from site-facing interfaces and either LISP-encapsulates packets to remote LISP sites, or natively forwards packets to non-LISP sites.

ETR (Egress Tunnel Router) - Registers its EID prefixes and RLOCs with the Map-Server, and responds to map requests received from the Map-Server. On the data plane side, an ETR receives packets from core-facing interfaces, de-encapsulates them, and delivers them to local EIDs at the site. 

xTR - Performs both ITR/ETR functions. 

PxTR - (Proxy xTR) Accepts encapsulated traffic from LISP sites and forwards natively to non-LISP sites. Draw non-LISP traffic to itself by announcing aggregates of EID prefixes to non-LISP core. 

MS (Map Server) - An MS receives Map-Registration messages from LISP sites. It also receives Map-Requests (via the Mapping System) seeking mapping resolutions for EID prefixes and forwards them to the registered ETR that is authoritative for the EID prefix being queried.

MR (Map Resolver) - An MR receives map requests from ITRs and forwards them to the Mapping System (resulting in an MS receiving the Map-Request). An MR also sends negative map replies to ITRs in response to queries for non-LISP addresses.

