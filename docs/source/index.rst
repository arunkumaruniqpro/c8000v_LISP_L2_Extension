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


