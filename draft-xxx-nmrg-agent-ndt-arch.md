---
title: "Integrating Generative AI with Network Digital Twin for Network Operation"
abbrev: "AI Agent archiecture"
category: info

# Network Digital Twin based Architecture for Service oriented AI for Network Operation
# AI driven Network Digital Twin Management Framework
# Architecture for integrating Generative AI with Network Digital Twin

docname: draft-xxx-nmrg-agent-ndt-arch-latest
submissiontype: IRTF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
area: ""
workgroup: "Network Management"
keyword:
 - network digital twin
 - Large Language Model
 - architecture
 - network management

author:
-
   fullname: Qin Wu
   organization: Huawei
   street: 101 Software Avenue, Yuhua District
   city: Jiangsu
   code: 210012
   country: China
   email: bill.wu@huawei.com

normative:

informative:


--- abstract

A Network Digital Twin (NDT) provides a network emulation tool for
scenario planning, impact analysis, and change management. Integrating
a Network Digital Twin into network management together with AI, intent allows intent based management
take user intent data or service requirements as input,
automatically assess, model, and refine optimization strategies under real conditions
but in a risk-free environment. An environment that operates to meet these types of
requirements is said to have service oriented AI for Network Operations.

AI for Network Operation brings together existing technologies such
as network digital twin, AI and may be seen as the use of a toolbox
of existing components enhanced with a few new elements.

This document describes an architecture and framework for service oriented AI for Network
Operation, showing how these components work together. It provides a
cookbook of existing technologies to satisfy the architecture and realize
intent based networking to meet the needs of the applications.

--- middle

# Introduction

The rapid expansion of network scale and the increasing demands on these networks necessitate
making network change better adapt to ever-changing service requirements.

Since network changes are directly related to service operations, any successful change
needs to not only ensure that new services are provisioned smoothly, but also that existing
services are not affected and that no problems are introduced. Network operators or O&M personnel
are, therefore, increasingly cautious about making network changes, given that they need to review
the solution design as well as evaluate all change impacts, before making any change. Then, after
the change, they need to perform dialing tests, monitor traffic, and manually check table entries.

A Network Digital Twin (NDT) {{?I-D.irtf-nmrg-network-digital-twin-arch}} was developed to provide a
network emulation tool for scenario planning, impact analysis, and change management. Integrating
a Network Digital Twin into network management together with AI, intent allows network management
dynamically adapt to customer needs,
automatically assess, model, and refine optimization strategies under real conditions
but in a risk-free environment. An environment that operates to meet these types of
requirements is said to have service oriented AI for Network Operations.

service oriented AI for Network Operations provide the following types of service to applications by
coordinating the components that operate and manage the network:

* Network intent and service assurance work together to ensure that the
  network change aligns with business goals and that the services provided
  meet the agreed-upon Service Level Agreements (SLAs).

* Models the protocol operations and interactions among devices in the network and Simulating specific
  networking protocols such as IS-IS, OSPF, BGP, SR to understand how they perform under
  different conditions.

* Modelling traffic flow across the network, including packet generation, flow control, routing, and
  congestion. It aims to evaluate traffic's impact on network performance.

* Network Capacity planning to ensure that the network has sufficient capacity
  , resources, and infrastructure to meet current and future demands.

This document describes an architecture and framework for service oriented AI for Network
Operation, showing how these components work together. It provides a
cookbook of existing technologies to satisfy the architecture and realize
intent based networking to meet the needs of the applications.



# Conventions and Definitions

{::boilerplate bcp14-tagged}


# Introduction of Concepts

## AI Agent

## Network Digital Twin


# AI for Network Operation

## Assumptions

The principal assumption underlying this document is that existing
technologies should be used where they are adequate for the task.
Furthermore, when an existing technology is almost sufficient, it is
assumed to be preferable to make minor extensions rather than to
invent a whole new technology.

Note that this document describes an architecture.  Functional
components are architectural concepts and have distinct and clear
responsibilities.  Pairs of functional components interact over
functional interfaces that are, themselves, architectural concepts.

# archiecture Design

## Overall Archiecture

{{arch}} provides the overall archiecture for integrating Network Digital Twin and Network Agent System.

~~~~
+--------------------------------------------------------------------+
|                                                                    |
|               OSS/Multi-domain Orchestrator                        |
+-----^-------------------^-------------^----------------------------+
      |                   |             |
+-----+-------------------+-------------+----------------------------+
| +---v----+     +--------+-------------+---------------------------+|
| |        |     |   +----+-------------+------------------------+  ||
| |        |     |   |+---v-----+ +-----v---+ +--------------+   |  ||
| |        |     |   ||Agent NBI| |Agent GUI| |Access Control|   |  ||
| |        |     |   |+---------+ +---------+ +--------------+   |  ||
| |        |     |   |                           AI Agent Access |  ||
| |        |     |   +-------------------------------------------+  ||
| |        |     |                                                  ||
| |        |     |      +-------------------------+                 ||
| |        |     |      |  +----------------------+---+             ||
| |Network |     |      |  | +------------------------+--+          ||
| |Digital <----->      +--+-+                        |  |          ||
| |Twin    |     |         | |        AI Agent(s)     |  |          ||
| |        |     |         +-+------------------------+  |          ||
| |        |     |           +--^------------^---------+-+          ||
| |        |     |              |            |         |            ||
| |        |     |              |            |         |            ||
| |        |     |        +-----v--+  +------v------+  |            ||
| |        |     |        |        |  |Knowledge and|  |            ||
| |        |     |        |   LLM  |  |Memory System|  |            ||
| |        |     |        +--------+  +-------------+  |            ||
| |        |     | Network Agent System                |            ||
| +----^---+     +-------------------------------------+------------+|
|      |                                               |             |
| +----v-----------------------------------------------v------------+|
| |                                                                 ||
| |    Original Management,Control, and Analysis Unit               ||
| +------------------------------^----------------------------------+|
|                                |         Network Management System |
+--------------------------------+-----------------------------------+
|                                |                                   |
+--------------------------------v-----------------------------------+
|                                                                    |
|                 Physical Network                                   |
+--------------------------------------------------------------------+
~~~~
{: #arch title="An Architecture for " artwork-align="center"}

## Functional Components

# AI in Network Operation: A collection of Use Cases

AI Agent could help in the following three phases which are usually mentioned in network management:

* Day 0: Network Planning and Design: includes the understanding of user intent,
         generation of solutions, and simulation for decision-making.
* Day 1: Service Deployment: includes the construction of the physical network,
         as well as intent understanding, pre-deployment simulation, automated configuration,
         post-deployment validation, and other capabilities to enhance the efficiency
         and accuracy of network configuration for service deployment.
* Day 2: Network Monitoring and Troubleshooting: includes intent monitoring, issues
         identification, solution generation, evaluation and decison-making, solution
         implementation, and service validation.
* Day N: Network Change and Optimization: involves the design, evaluation, decision-making,
         implementation, and validation of network configuration changes or optimizations
         to improve network operation efficiency.

## Network Configuration Change

## Network Troubleshooting

## Network Optimization

# Challenges and Future Work

## hallucination

Although Gen-AI can produce amazing results at first sight, sometimes they can be
totally wrong.

# Security Considerations

TODO Security

# Manageability Consideration

# IANA Considerations

This document has no requests to IANA.


--- back

# Acknowledgments
{:numbered="false"}

TODO Acknowledgments.
