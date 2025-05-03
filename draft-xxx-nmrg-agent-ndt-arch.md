---
title: "Network Digital Twin based Architecture for Service oriented AI for Network Operations"
abbrev: "AI Agent archiecture"
category: info

# Network Digital Twin based Architecture for Service oriented AI for Network Operation
# AI driven Network Digital Twin Management Framework
# Integrating Generative AI with Network Digital Twin for Network Operation
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

  TMF-1218:
    title: "Autonomous Networks Business Requirements and Framework"
    target: https://www.tmforum.org/resources/introductory-guide/autonomous-networks-business-requirements-and-framework-v3-0-0-ig1218
    date: May 2024

  TMF-1345:
    title: "Embracing Generative AI in Telecom: Amplifying Autonomous Network Evolution"
    target: https://www.tmforum.org/resources/introductory-guide/ig1345-embracing-generative-ai-in-telecom-amplifying-autonomous-network-evolution-v1-1-0
    date: Jan 2025

  ETSI-ENI035:
    title: "Experiential Networked Intelligence (ENI); Definition of IP networks autonomicity level"
    target: https://www.etsi.org/deliver/etsi_gr/ENI/001_099/035/
            04.01.01_60/gr_ENI035v040101p.pdf
    date: December 2023

--- abstract

A Network Digital Twin (NDT) provides a network emulation tool for
scenario planning, impact analysis, and change management. Integrating
a Network Digital Twin into network management together with AI, it allows the network management
activities to take user intent or service requirements as input,
automatically assess, model, and refine optimization strategies under real conditions
but in a risk-free environment. An environment that operates to meet these types of
requirements is said to have service oriented AI for Network Operations.

AI for Network Operations brings together existing technologies such
as Network Digital Twin and AI which may be seen as the use of a toolbox
of existing components enhanced with a few new elements.

This document describes an architecture and framework for service oriented AI for Network
Operations and shows how these components work together. It provides a
cookbook of existing technologies to satisfy the architecture and realize
intent based networking to meet the needs of the network service.

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
a Network Digital Twin into network management together with AI, it allows network management activities
to dynamically adapt to customer needs,
automatically assess, model, and refine optimization strategies under real conditions
but in a risk-free environment. An environment that operates to meet these types of
requirements is said to have service oriented AI for network operations.

Service oriented AI for Network Operations provide the following types of service to applications by
coordinating the components that operate and manage the network:

* Service intent and service assurance work together to ensure that the
  network change or network optimization aligns with business goals and that the services provided
  meet the agreed-upon Service Level Agreements (SLAs).

* Provide Network capacity planning and ensure that the network has sufficient capacity
  , resources, and infrastructure to meet current and future demands.

* Model the protocol operations and interactions among devices in the network and simulate specific
  networking protocols such as IS-IS, OSPF, BGP, SR to understand how they perform under
  different conditions.

* Model traffic flow across the network, including traffic generation, flow control, routing, and
  congestion control and evaluate traffic's impact on network performance.

This document describes an architecture and framework for service oriented AI for network
operations, showing how these components work together. It provides a
cookbook of existing technologies to satisfy the architecture and realize
intent based networking to meet the needs of the applications.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

The document uses the following definitions and acronyms defined in {{?I-D.irtf-nmrg-network-digital-twin-arch}}:

* Network Digital Twin (NDT)

* Artificial Intelligence (AI)

 The following acronyms are used throughout this document:

 * Generative Artificial Intelligence (Gen-AI)

 * Large Language Model (LLM)

 * Retrieval-Augmented Generation (RAG)

# Introduction of Concepts

## Generative AI and AI Agent

The integration of AI into network operations has marked a significant leap forward in
the pursuit of network automation and intelligence, while generative AI further
enhances the role of AI in network operations and management. Generative AI is a
subfield of AI that uses generative models such as LLMs to generate new and
original content such as text, images, videos, or other forms of data with the
capability to adapt and make decisions to achieve specific goals.
{{TMF-1218}} lists full-stack AI as one of key requirements of Autonomous Network capabilities,
and {{TMF-1345}} highlights the potential of generative AI in driving the evoluation
of autonomous networks. Other SDOs like ETSI (Experiential Networked Intelligence) ENI
is actively advancing the integration of AI in networks and services {{ETSI-ENI035}}.

AI agent which takes the power of generative AI a step further refers to a system
or program that uses AI to perform tasks on behalf of users.
AI Agent is an autonomous entity that can perceive the environment, make decisions,
and take actions to achieve specific goals. In the context of network operations
and management, agents are increasingly being designed to perform tasks such as
understanding user intent, generating network configurations, diagnosing and resolving network
incidents {{?I-D.ietf-nmop-network-incident-yang}}.

## Network Digital Twin

The Network Digital Twin is a digital representation that is used in the context
of network. The concept and archiecture of the Network Digital Twin are specified
in {{I-D.irtf-nmrg-network-digital-twin-arch}}. Three core functional components
which includes Data Repository component, a Service Mapping Models component,
and an NDT Management component are introduced to characterize the Network Digital
Twin and its reference architecture.

The Network Digital Twin is widely recognized to be useful as an advanced platform
for network emulation, serving as a tool for scenario planning, impact analysis,
and change management. By delivering applications requests to the Network Digital
Twin through standardized interfaces (see
{{Section 9.4 of ?I-D.irtf-nmrg-network-digital-twin-arch}}), the Network Digital
Twin exposes the various capabilities to network applications.

# Characteristics of AI for Network Operations

AIOPS was first defined by Gartner in 2016, combining "artificial intelligence"
and "IT operations" to describe the application of AI and machine learning to
enhance IT operations. However there is no unified definition for characteristic
of "AI for network operations" within the networking industry.  Referring to the
characteristics of AIOPS in IT field and the characteristics of networking itself,
this document introduces six key elements (i.e., awareness, decision, analysis, execution, intent and knowledge) to
characterize the AI for network operation and its use, as shown in {{ops-arch}}.
They together form a close-loop of network operation and management.

~~~~
 +---------------------------------------------------+
 |                  +---------+                      |
 |                  |  Intent |                      |
 |                  +---------+                      |
 |                                                   |
 | +-----------+                       +-----------+ |
 | |  Decision |                       | Analysis  | |
 | +-----------+       --------        +-----------+ |
 |                 ////        \\\\                  |
 |                |AI for Network  |                 |
 |                |  Operations    |                 |
 |                 \\\\        ////                  |
 |                     --------                      |
 | +-----------+                      +------------+ |
 | |  Awareness|                      |  Excution  | |
 | +-----------+                      +------------+ |
 |                                                   |
 |                 +-----------+                     |
 |                 | Knowledge |                     |
 |                 +-----------+                     |
 +---------------------------------------------------+
~~~~
{: #ops-arch title="Six Key Elements to Characterize AI for network operation" artwork-align="center"}

* Intent:
: Intent is defined as a set of operational goals and outcomes defined in a declarative
  manner without specifying how to achieve or implement them in {{?RFC9315}}. The AI agent
  must accurately intepret and understand the user's high-level business or operational
  objectives, this involves translating declarative requirements into specific network
  instructions, e.g., configurations.

* Decision:
: Based on the intent and network analysis, the AI agent makes
  informed decisions. These decisions could involve dynamically adjusting network
  parameters, e.g., rerouting traffic to avoid congestion. The decision-making
  process is driven by predefined policies, real-time data analysis, and AI
  models (e.g., LLMs) that enable the AI agent to choose the best course of action
  to meet the specified intent. AI agent may also verify the correctness the decision
  by performing some network simulation or validation process.

* Analysis:
: The AI agent continuously analyzes vast amounts of network data from various
  source, including network telemetry {{?RFC9232}} and external feeds, and identify
  the gap between user intent and the existing network status. Leveraging machine
  learning and other data analytics techniques, it also identifies
  network fault, problem, incident, anomaly, and so on. Their distinction is further
  discussed in {{?I-D.ietf-nmop-terminology}}.

* Awareness:
: Awareness is achieved through real-time monitoring and data collection.
  The AI agent maintains a comprehensive visibility of the network,
  enabling it to make context-aware decisions. Network operators can also use the
  awareness understand the root cause of specific network issues and achieve closed-loop
  decision-making.

* Execution:
: Once a decision is made, the AI agent executes the necessary actions to implement
  it. This could involve, e.g., sending configuration to network devices through
  NETCONF/RESTCONF protocols. The execution is carried out in a controlled and
  precise manner to ensure that the network behaves as intended without causing
  disruptions. The AI agent also verifies that the executed actions have the
  desired effect and makes adjustments if needed.

* Knowledge:
: The AI agent relies on a knowledge base that includes network policies,
  historical data, expert experience, and best practices in product manual. The
  knowledge is used to inform its analysis, decision-making, and execution processes.
  Over time, the AI agent can expand its knowledge through machine learning,
  incorporating new data and experiences to improve its performance. For example,
  it learns which configurations are optimal for specific scenarios or how to
  respond most effectively to particular types of network incidents {{?I-D.ietf-nmop-network-incident-yang}}.

# archiecture Design

## Overall Archiecture

{{arch}} provides the overall archiecture for integrating Network Digital Twin and Network Agent System.

~~~~
+----------------------------------------------------------------------+
|                 Multi-domain Orchestrator                            |
+------------------^-----------------------^---------------------------+
                   |                       |
        Invoke NDT |       Intent Interface|
+------------------+-----------------------+---------------------------+
|Autonomous Domain |                       |                           |
| +----------------v------+        +-------v---------+                 |
| |                       |        |Intent Management|                 |
| |                       |        +-------+---------+                 |
| |                       |                |                           |
| |                       |                |                           |
| |                       |                |                           |
| |                       |        +-------v---------+    +-----------+|
| |                       |        |   AI Agent(s)   |    | Knowledge ||
| |                       <-------->   (Analysis &   <----> Base      ||
| | Network Digital Twin  |   +---->    Decision)    |    |           ||
| |                       |   |    +-----------+-----+    +-----------+|
| |                       |   |                |                       |
| |                       |   |                |                       |
| |                       |   |                |                       |
| |                       |   |                |                       |
| |                       |   |                |                       |
| |                       |   |                |                       |
| |                       |   |                |                       |
| +-------------------^---+   |                |                       |
|                     |       |                |                       |
|                +----+-------+---+      +-----v----------+            |
|                |                |      |                |            |
|                | Data Collection|      |    Execution   |            |
|                |                |      |                |            |
|                +--------^-------+      +-------+--------+            |
+-------------------------+----------------------+---------------------+
                          |                      |
                          |                      |
+-------------------------+----------------------v---------------------+
|                    Physical Network                                  |
+----------------------------------------------------------------------+
~~~~
{: #arch title="An Architecture for Integrating Generative AI with Network Digital Twin" artwork-align="center"}

## Functional Components

### Multi-domain Orchestrator

### Autonomous Domain

#### Network Digital Twin

#### Intent Management

 this includes NBI, GUI, access management.

#### AI Agent(s)

Agents could be scenario-oriented and classified according to the function they perform.

#### Knowledge Base

#### Data Collection

#### Execution

### Physical Network


## Architecture Requirements

There are a couple of key requirements of the architecture to integrate
Network Digital twin with service-oriented AI which are crucial in
ensuring the proposed architecture can handle the complex and dynamic network scenarios
for network operations and management.

## Human-in-the-loop

This allows human experts to provide guidance and make critical decisions when necessary.
By involving human in the process, the archiecture can leverage their insights and
experience, ensuring AI actions align with organizational goals.

## Interoperability via Open Standards

standardized protocols and interfaces facilitate smooth communication from various vendors.

## Feedback-driven Improvement

## Scalability and Flexibility


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

## Security

# Security Considerations

TODO Security

# IANA Considerations

This document has no requests to IANA.


--- back

# Acknowledgments
{:numbered="false"}

TODO Acknowledgments.
