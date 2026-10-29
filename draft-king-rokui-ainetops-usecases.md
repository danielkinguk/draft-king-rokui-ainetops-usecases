---
title: "Artificial Intelligence (AI) for Network Operations"
abbrev: "AINetOps Use Cases"
category: info

docname: draft-king-rokui-ainetops-usecases-latest
submissiontype: IETF  # also: "independent", "editorial", "IAB", or "IRTF"
number:
date:
consensus: true
v: 3
# area: AREA
# workgroup: "RTG"
keyword:
 - AI
 - ML
 - Artificial Intelligence
 - Use Cases

author:
-
  fullname: Reza Rokui
  organization: Ciena
  email: rrokui@ciena.com
-
  fullname: Daniel King
  organization: Lancaster University
  email: d.king@lancaster.ac.uk
-
  fullname: Cheng Li
  organization: Huawei
  email: c.l@huawei.com
-
  fullname: Qin Wu
  organization: Huawei
  email: bill.wu@huawei.com

contributor:
-
  fullname: Daniele Ceccarelli
  organization: Cisco
  email: dceccare@cisco.com
-
  fullname: Arashmid Aakhavain
  organization: Huawei
  email: arashmid.akhavain@huawei.com
-
  fullname: Oscar González de Dios
  organization: Telefonica
  email: oscar.gonzalezdedios@telefonica.com
-
  fullname: Ignacio Dominguez Martinez-Casanueva
  organization: Telefonica
  email: ignacio.dominguezmartinez@telefonica.com
-
  fullname: Vincenzo Riccobene
  organization: Huawei
  email: vincenzo.riccobene@huawei-partners.com
-
  fullname: Nathalie Romo-moreno
  organization: Telekom
  email:  nathalie.romo-moreno@telekom.de
-
  fullname: Ali Tizghadam
  organization: Telus
  email: ali.tizghadam@telus.com
-


normative:

informative:

 ICON:
   title:  Observability, Intervention and Control of Network Management Agent
   target: https://github.com/billwuqin/Agent-Observability-Intervention-Control
   date: 2026

--- abstract

This document explores the role of the IETF and IRTF in advancing
Artificial Intelligence for network operations (AINetOps), focusing on
requirements for IETF protocols and architectures. AINetOps applies AI/ML
techniques to automate and optimize network operations, enabling use
cases such as reactive troubleshooting, proactive assurance, closed-loop
optimization, misconfiguration detection, and virtual operator
assistance. In addition, AINetOps also introduces network management agents
which make AI native operations non-deterministic, therefore constraining
the behavior of AI agents within operational and compliance boundaries become
extremely important.

The document addresses AINetOps challenges for both single-layer IP or Optical
networks and multi-layer IP/Optical networks. It defines the concept of
AINetOps for networking and provides its operational benefits such as
network assurance, predictive analytics, network optimization,
multi-layer planning, and more. It aims to guide the evolution of IETF
protocols to support AINetOps-driven network management.


--- middle

# Introduction

The increasing complexity of modern networks has driven the need for
innovative approaches to network operations and management. Artificial
Intelligence for Network Operations (AINetOps) has emerged as an
innovative concept, leveraging artificial intelligence (AI) and
machine learning (ML) to automate, enhance, and optimize network
management tasks. AINetOps offers the potential to reduce operational
costs, improve service reliability, and enhance user experiences by
enabling intelligent automation, predictive insights, and efficient
decision-making.

The IETF and IRTF play a critical role in defining the protocols,
architectures, and standards that underpin global networking. As AINetOps
becomes integral to network operations, there is a growing need to
evaluate how existing IETF technologies can support AINetOps use cases
and to identify gaps that may require new or extended solutions. This
document aims to outline key AINetOps use cases, highlight associated
technical challenges, and propose requirements for protocols and
architectures to address these challenges effectively.

The use cases considered in this document span across multiple phases of
network operations, including reactive troubleshooting, proactive
assurance (e.g., anomaly detection, predictive maintenance), closed-loop
optimization, and misconfiguration detection. Emerging capabilities, such
as generative AI for operational insights and virtual operator
assistants, further emphasize the need for a robust framework to support
AI-driven network management. Additionally, the multi-layered nature of
these use cases, encompassing IP, optical, and cross-layer optimization,
underscores the complexity of integrating AINetOps into existing
networks.

This document provides a foundation for advancing IETF protocols and
architectures to enable AINetOps-driven network operations and prevent
non-deterministic outcome introduced by AINetOPs by exploring
these use cases, the requirements, and their implications.

## Background

Efficient and coordinated use of resources is paramount for maintaining
optimal performance and reliability of many network environments. The applicability
of Artificial Intelligence is well-established, and the use cases are outlined
in this document.

## Prior and Related IETF and IRTF Work

   The IETF has already standardized an autonomic networking
   architecture that is directly relevant to AINetOps.  The Autonomic
   Service Agent (ASA) model, the Autonomic Control Plane, and the GRASP
   protocol {{?RFC8990}} were designed for autonomous, policy-driven agents
   operating in network infrastructure; AI-based agents can be viewed as
   a more capable instantiation of that model rather than a departure
   from it.

   In the IRTF, the Network Management Research Group (NMRG) has
   examined the research challenges of coupling AI with network
   management {{?I-D.irtf-nmrg-ai-challenges}} and has proposed a framework
   for LLM-assisted network management with a human-in-the-loop
   {{?I-D.irtf-nmrg-llm-nm}}.

   A number of related individual drafts are active in this space:

   *  A governance framework for AI-mediated autonomous network device
      management {{?I-D.smith-opsawg-ai-network-governance}}.

   *  An AI-based Network Management Agent (NMA) concept and
      architecture {{?I-D.zhao-nmop-network-management-agent}}, with a
      companion YANG data model for its Agent-to-User (A2U) interface
      {{?I-D.zhao-nmop-nma-a2u-yang}}.

   *  Applicability and gap analyses of NETCONF/RESTCONF for AI-driven
      operations, and proposed Model Context Protocol (MCP) extensions
      for network equipment management
      {{?I-D.zeng-opsawg-applicability-mcp-a2a}},
      {{?I-D.zeng-opsawg-llm-netconf-gap}},
      {{?I-D.zw-opsawg-mcp-network-mgmt}}.

   *  A canonical semantic representation intended to bridge YANG data
      models and the semantic framing needed by LLM-based agents
      {{?I-D.feng-netmod-naim}}.

   *  A GRASP-based agent rendezvous mechanism
      {{?I-D.carpenter-anima-grasp-rendezvous}}.

   *  An agent communication framework and registry for network AIOps
      {{?I-D.fu-nmop-agent-communication-framework}} and a problem
      statement on model grounding and token operations
      {{?I-D.fu-nmop-tokenops-probelem-statement}}, both based on operator
      deployment experience.

   In addition, the ICON (Observability, Intervention and Control of
   Network Management Agent) effort {{ICON}} is exploring how network
   management agents can be continuously monitored, intervened upon, and
   controlled when they misbehave, including trajectory records of agent
   behavior, human oversight, and standardized intervention and recovery
   mechanisms.  Section 7 discusses these considerations as they apply
   across the use cases in this document.

   Discussion of the integration of AI/ML into network operations using
   IETF technologies takes place on the AINETOPS non-working-group
   mailing list (ainetops@ietf.org).

## Scope

   This document describes use cases and identifies associated
   requirements.  It is intended to scope, ground, and prioritize
   subsequent normative work, such as YANG data models, protocol
   extensions, and operational guidance, rather than to serve as a
   standalone endpoint.

   The specification of AI and ML algorithms, AI model architectures, and
   training methodologies is out of scope for this document.  The use
   cases and requirements described here are intentionally agnostic to
   any particular AI technique or implementation.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

The following terms are used in this document:

* AI:
: Artificial Intelligence aims to create systems capable of performing
tasks that typically require human intelligence, such as understanding
natural language, recognizing patterns, and making decisions.

* ML:
: Machine Learning is a subset of AI that involves training algorithms on
large datasets to enable them to learn patterns and make predictions or
decisions without being explicitly programmed.

* Gen-AI:
: Generative-AI is a subset of ML techniques that creates new content, such
as text, images, or audio, by learning from existing data.

* NLP:
: Natural Language Processing is a field of AI that focuses on the
interaction between computers and humans through natural language.

* AINetOps:
: Artificial Intelligence for Network Operations refers to the application
of AI, ML, and generative-AI techniques to enhance and automate network operations.

* Closed-Loop Optimization:
: Automated feedback-driven processes for continuously improving network
performance and reliability.

* Multi-Layer Optimization:
: Addressing cross-layer dependencies and optimizing
resources across different network layers, such as IP and optical layers.

* P-PNC: Packet Provisioning Network Controllers

* O-PNC: Optical Provisioning Network Controllers

* MDSC: Multi-Domain Service Coordinator

# AI, ML, Deep Learning, Gen-AI, Agentic AI

   Artificial Intelligence (AI) is the broad field dedicated to creating
   systems that can perform tasks typically requiring human
   intelligence, such as reasoning, problem-solving, and understanding
   language.  Within AI, Machine Learning (ML) is a subset that focuses
   on developing algorithms that enable computers to learn from and make
   decisions based on data, improving their performance over time
   without explicit programming.  Deep Learning is a further subset of
   ML that utilizes neural networks with many layers (hence "deep") to
   analyze various factors of data.  This approach is particularly
   powerful in handling large and complex datasets, making significant
   advancements in areas such as image and speech recognition, natural
   language processing, and autonomous systems.

   Generative AI (Gen-AI) is a specialized branch of ML that involves
   training models to generate new content, such as text, images, or
   music, by learning patterns from existing data, thereby enhancing the
   creative and adaptive capabilities of AI systems.  Deep Learning
   techniques are often employed in Gen-AI to create more sophisticated
   and realistic outputs, pushing the boundaries of what AI can achieve
   in terms of creativity and innovation.

   agentic AI autonomously plans and executes multi-step workflows to
   achieve a specific goal. Generative AI focuses on creation (text,
   images, code). Agentic AI focuses on action, decision-making, and
   problem-solving.

   {{fig1}} shows the relationship between AI, ML, Deep Learning, and
   Gen-AI.

~~~~
          |-------------------------------------|
          |                  AI                 |
          |   |-----------------------------|   |
          |   |              ML             |   |
          |   |   |---------------------|   |   |
          |   |   |    Deep Learning    |   |   |
          |   |   |   |-------------|   |   |   |
          |   |   |   |   Gen-AI    |   |   |   |
          |   |   |   | +--------+  |   |   |   |
          |   |   |   | | Agentic|  |   |   |   |
          |   |   |   | |   AI   |  |   |   |   |
          |   |   |   | +--------+  |   |   |   |
          |   |   |   +-------------+   |   |   |
          |   |   |---------------------|   |   |
          |   |-----------------------------|   |
          |-------------------------------------|
~~~~
{: #fig1 title="Relationship between AI, ML, Deep Learning, Gen-AI, Agentic AI" artwork-align="center"}

# Definition of AINetOps

   Figure 2 illustrates the concept of AI for Network Operations
   (AINetOps), which leverages AI, ML, Gen-AI, Agentic AI techniques and rule-based
   systems to enhance and automate network operations.  By integrating
   both historical and real-time streaming data, AINetOps employs
   advanced data analytics to uncover hidden patterns, establish data
   correlations, and provide trend forecasts and anomaly detection.
   These insights lead to significant operational benefits, including
   improved network performance, reduced downtime, and more efficient
   management of IP optical networks.  Additionally, AINetOps enables
   proactive and predictive analytics, allowing network operators to
   address potential issues before they impact users, thereby ensuring
   more resilient and reliable network operations.

   This document introduces the term "Operational Benefit", which
   encompasses the comprehensive suite of tools and methodologies that
   facilitate the efficient management, debugging, troubleshooting,
   monitoring, configuration, and optimization of IP Optical networks.
   These operational benefits might include network management systems,
   automated diagnostic tools, performance monitoring and telemetry
   systems, configuration management platforms, and optimization
   algorithms.  By leveraging these resources, operators can ensure the
   robust performance, reliability, and scalability of the network,
   ultimately enhancing service delivery and reducing operational costs.
   The integration of these operational benefits is crucial for
   maintaining seamless network operations and achieving strategic
   business objectives.

   Section 5 expands the operational benefits shown in Figure 2 and
   provides a detailed explanation of the various operational benefits
   offered by AINetOps.

   {{fig2}} shows the definition of AINetOps.

~~~~
    |------------|    |--------------|     |-----------------------|
    |            |    |  AI /        |     |                       |
    |    Big     |    |  ML /        |     |                       |
    |    Data    |  + |  Gen-AI/     |  =  |        AINetOps       |
    |            |    |  Agentic AI/ |     |                       |
    |            |    |  Rule-based  |     |                       |
    |            |    |              |     |                       |
    |------------|    |--------------|     |-----------------------|
                                               AINetOps provides
                                               Operational Benefits
      Big Data: Historical or Real-time data
               (e.g., time series PM, Alarm, Topology, Log,
                OAM data, product content/documentation etc.)
~~~~
{: #fig2 title="Definition of AINetOps" artwork-align="center"}

# Operational Benefits Provided by AINetOps

AINetOps has the potential to revolutionize network operations by
addressing the inherent complexity, scale, and dynamic nature of
modern networks.  By applying various AI/ML/Gen-AI techniques,
network operators can transition from traditional manual or rule-
based operations to intelligent, automated systems capable of real-
time adaptation, predictive insights, and optimized decision-making.

In addition, human on the loop has been integrated into the AI-driven
IP network management and operation loop, which allow the system execute
network operations autonomously while human operators monitor outcomes,
enforce governance policies, and intervene only for exceptional or
high-risk situations. With Human on the loop,  uncertain or ambiguous
network operations or tasks can be tackled.

This section outlines the following key areas where AINetOps can be
applied effectively in network operations, leveraging both data-
driven models and domain-specific knowledge.

* Section 5.1 "Operator Network Assistance"

* Section 5.2 "Network Active and Reactive Assurance".  This area is also
   related to "Root Cause Analysis" Section 5.2.1

* Section 5.3 "Predictive Analytics" which includes "Proactive
   Network Assurance and Monitoring" Section 5.3.1, "Anomaly
   Detection" Section 5.3.2, "Trending and Forecasting"
   Section 5.3.3, "Predictive Maintenance" Section 5.3.4 and "Network
   Capacity Planning" Section 5.3.5

* Section 5.4 "Network Operational Insights".  This area can be
   grouped into "Operational Insights Requiring No Further Analysis"
   Section 5.4.1 and "Operational Insights Requiring Further Analysis"
   Section 5.4.2

* Section 5.5 "Network Configuration Management"

* Section 5.6 "IP/Optical Multi-layer Planning"

* Section 5.7 "Cross-Layer and Multi-Layer Optimization"

* Section 5.8 "Traffic Optimization"

* Section 5.9 "Closed-Loop Automation"

* Section 5.10 "Network Maintenance and Cleanup"

* Section 5.11 "Network API Construction"

* Section 5.12 "AI-Driven Security Monitoring"

* Section 5.13 "Multi-Agent Interworking"

## Operator Network Assistance

   Powered by Gen-AI, the operator network assistant functions as a
   virtual network engineer, providing real-time recommendations,
   insights, and automated solutions.  These systems use NLP for
   interface interaction, deep learning for anomaly classification, and
   contextual understanding to enhance operator decision-making.

   AI-powered operator assistants function as virtual network engineers,
   providing real-time recommendations, insights, and automated
   solutions.  These advanced systems leverage the power of natural
   language processing (NLP) to facilitate seamless and intuitive
   interactions between operators and the network management interface.
   By understanding and interpreting human language, these AI assistants
   can effectively communicate with operators, making it easier for them
   to manage complex network environments without needing extensive
   technical expertise.

   In addition to NLP, Operator Assistance can integrate other AINetOps
   functions to solve operator scenarios and use-cases.  This
   capability allows the system to provide timely alerts and
   recommendations, helping operators to address issues before they
   escalate into major disruptions.  The deep learning models
   continuously improve over time, becoming more adept at recognizing
   new types of anomalies and adapting to evolving network conditions.

   Furthermore, the contextual understanding capabilities of AI-powered
   operator network assistant significantly enhance operator decision-
   making.  By considering the broader context of network operations,
   including historical data, current network state, and external
   factors, the AI can offer more relevant and actionable insights.
   This holistic approach ensures that operators receive comprehensive
   guidance tailored to the specific circumstances of their network.  As
   a result, operators can make more informed decisions, optimize
   network performance, and maintain high levels of service reliability
   and efficiency.  In essence, AI-powered operator network assistants
   are transforming network management by augmenting human capabilities
   with advanced technology, leading to smarter and more proactive
   network operations.

## Network Active and Reactive Assurance

   Network Active and Reactive Assurance and troubleshooting, both at the single-
   layer (IP or Optical) and multi-layer (IP over Optical), are critical
   components in maintaining the health and stability of modern IP,
   Optical, and IPoDWDM networks.  This process involves the
   identification and resolution of network issues as they arise,
   ensuring that any disruptions or degradations are promptly addressed.
   By employing AINetOps techniques, network engineers can quickly
   pinpoint the root cause of problems, whether they originate in the IP
   layer, the optical layer, or across both.  This reactive approach is
   essential for minimizing downtime and maintaining the quality of
   service expected by network users.

   In single-layer troubleshooting, the focus is on isolating and
   resolving issues within a specific layer of the network.  For
   example, in an IP network, this might involve diagnosing routing
   problems, addressing IP address conflicts, IP layer misconfiguration,
   hardware failure or resolving issues with network protocols.  In an
   optical network, single-layer troubleshooting could involve
   identifying fiber cuts, optical signal degradation, or equipment
   failures

   Multi-layer troubleshooting, on the other hand, requires a more
   integrated approach, as it involves identifying and resolving issues
   that span across multiple layers of the network.  This could include
   problems where an issue in the optical layer affects the IP layer,
   such as signal impairments that impact data transmission quality.  By
   effectively managing both single-layer and multi-layer
   troubleshooting, network engineers can ensure a more robust and
   resilient network infrastructure.

   The importance of assurance and troubleshooting cannot be
   overstated in today's high-demand network environments.  Rapid
   response to network issues is crucial to maintaining service
   continuity and meeting the expectations of end-users.  Advanced
   diagnostic tools and techniques, such as real-time monitoring,
   automated alerts, and detailed analytics, play a vital role in this
   process.  These tools enable engineers to quickly detect anomalies,
   assess their impact, and implement corrective actions.  Through
   continuous improvement of assurance and troubleshooting
   practices, network operators can enhance their ability to maintain
   network performance, reduce operational risks, and deliver a reliable
   and high-quality service to their customers.

### Root Cause Analysis

   In the context of "Network Active and Reactive Assurance," Root Cause Analysis
   (RCA) is a critical aspect that extends the reactive troubleshooting
   process to uncover the underlying reasons behind network issues.
   When an issue is detected in the network, RCA leverages advanced
   AINetOps techniques to correlate events across different layers of
   the network, whether it be IP, Optical, or a combination of both.
   This comprehensive approach ensures that the root cause of an issue
   is accurately identified, rather than just addressing the symptoms.
   Techniques such as graph-based analysis enable network engineers to
   visualize and trace the sequence of events leading to a problem,
   providing a clear pathway to the source of the issue.

   Moreover, natural language processing (NLP) for log analysis plays a
   significant role in RCA by automating the examination of vast amounts
   of log data generated by network devices.  NLP can sift through logs
   to identify patterns and anomalies that might be missed by manual
   inspection.  This capability is particularly useful in multi-layer
   networks where issues in one layer can propagate and manifest in
   another.  By efficiently parsing through logs and correlating data,
   NLP helps pinpoint the exact cause of disruptions, thereby reducing
   the mean time to resolution (MTTR).  Additionally, knowledge graph
   representations provide a structured and interconnected view of
   network components and their relationships, aiding in the rapid
   identification of fault points and their impact on the network.

   By accurately diagnosing the root cause of network issues, network
   operators can implement targeted corrective actions that address the
   core problem, preventing recurrence and ensuring long-term stability.
   This precision in troubleshooting not only minimizes downtime but
   also enhances the overall reliability and performance of the network.
   Furthermore, insights gained from RCA can inform proactive measures
   and optimization strategies, contributing to a more resilient network
   infrastructure.  In essence, RCA empowers network engineers with the
   tools and knowledge needed to maintain high service quality and meet
   the demands of modern, high-performance networks.

## Predictive Analytics

   Predictive analytics or advanced analytics uses historical and real-
   time network data, statistical algorithms, and ML techniques to
   identify the likelihood of future outcomes based on past data.  In
   the context of network operations, predictive analytics involves the
   use of these methodologies in the following areas to anticipate network
   issues, optimize performance, and improve operational efficiency.  By
   examining patterns and trends in historical network data, predictive
   analytics can potentially forecast network problems before they
   occur, allowing for proactive management and maintenance.

   The core idea behind predictive analytics is to transform data into
   actionable insights.  For network operations, this means analyzing
   various metrics such as traffic patterns, latency, performance
   management (PM) data, and equipment performance to predict future
   states of the network.  For instance, by identifying trends that have
   historically led to network failures, predictive analytics can alert
   operators to potential future failures, enabling them to take
   preventive measures.  This proactive approach helps in minimizing
   downtime, enhancing service reliability, and optimizing resource
   allocation.

   In summary, predictive analytics in network operations is about
   leveraging historical data and advanced analytical techniques to
   foresee and address potential issues before they impact the network.
   This approach leads to more efficient, reliable, and secure network
   operations, ultimately enhancing the overall performance and user
   experience.  AINetOps can address the following operator
   scenarios.

### Proactive Network Assurance and Monitoring (Health Check)

   Proactive Network Assurance and Monitoring represents a paradigm
   shift from the Network Active and Reactive Assurance discussed in Section 5.2.
   Instead of waiting for issues to arise and then addressing them,
   proactive network assurance involves anticipating potential problems
   and implementing measures to prevent them from occurring.  This
   forward-thinking strategy leverages AINetOps to predict and mitigate
   network issues before they impact service quality.

   In single-layer proactive assurance, the focus is on continuously
   monitoring and analyzing the health of a specific layer (IP or Optical)
   of the network to identify early warning signs of potential
   issues.  For instance, in an IP network, this might involve analyzing
   traffic patterns to detect anomalies that could indicate an impending
   routing problem or hardware failure.  ML algorithms can be employed
   to predict IP address conflicts or protocol misconfigurations before
   they cause disruptions.  Similarly, in an optical network, proactive
   assurance could involve monitoring signal quality and fiber integrity
   to detect and address degradations before they lead to significant
   impairments or outages.

   Multi-layer proactive assurance takes this approach a step further by
   integrating monitoring and analysis across both the IP and optical
   layers.  This holistic view allows for the detection of complex
   issues that span multiple layers, such as optical signal impairments
   that could degrade IP data transmission quality.  By correlating data
   from both layers, an AINetOps solution can provide insights into how
   changes in the optical layer might affect IP performance and vice
   versa.  This enables operators to take preemptive actions, such as
   optimizing signal paths or adjusting routing protocols, to maintain
   optimal network performance.

   The benefits of proactive network assurance and monitoring are
   substantial.  By identifying and addressing potential issues before
   they escalate, network operators can significantly reduce downtime
   and improve service reliability.  This proactive stance not only
   enhances the user experience by ensuring consistent network
   performance but also reduces operational costs associated with
   emergency troubleshooting and repairs.  Furthermore, the use of
   advanced analytics and machine learning in AINetOps allows for
   continuous learning and improvement, enabling networks to become more
   resilient and adaptive over time.

   In today's dynamic and high-demand network environments, proactive
   network assurance and monitoring is one of the operational benefits
   provided by AINetOps and are essential for staying ahead of potential
   issues and maintaining a competitive edge.  By leveraging the power
   of AINetOps, network operators can transform their approach from
   reactive to proactive, ensuring that their networks are not only
   robust and resilient but also capable of delivering the high-quality
   service that users expect.  This shift towards proactive assurance
   represents a significant advancement in network management, paving
   the way for more intelligent, efficient, and reliable network
   operations.

### Anomaly Detection

   A critical component of AINetOps in the context of predictive
   analytics is "Anomaly Detection", which leverages advanced ML
   algorithms to enhance network reliability and performance.  By
   employing ML techniques such as supervised, unsupervised or
   reinforcement learning, AINetOps can predict anomalies in real-time
   by analyzing vast amounts of network telemetry data.  Supervised
   learning models, trained on historical data, recognize known issues,
   while unsupervised models identify new anomalies by spotting
   outliers.  This comprehensive detection mechanism ensures both
   familiar and novel network issues are identified promptly.
   Predictive models, utilizing techniques like time-series forecasting,
   enable the identification of potential network problems, such as link
   failures or traffic congestion, before they occur.  By forecasting
   future network states based on historical and current data, these
   models provide early warnings, allowing for timely interventions to
   prevent unexpected downtime and maintain optimal performance.

   Clustering techniques further enhance anomaly detection by grouping
   similar data points to identify patterns and trends that signal
   imminent failures or suboptimal behavior.  This method allows ML
   models to discern subtle changes in network behavior that might
   otherwise go unnoticed.  For example, clustering can reveal traffic
   congestion patterns under specific conditions, enabling preemptive
   measures to alleviate potential issues.  Additionally, clustering
   helps identify the root causes of anomalies by correlating various
   network events and metrics, facilitating a more effective
   troubleshooting process.  By integrating these advanced ML
   techniques, AINetOps not only improves anomaly detection but also
   empowers network operators with the insights needed to maintain a
   high-performing and reliable network infrastructure.

### Trending and Forecasting

   The "Trending and Forecasting" operational benefit is distinct but is
   related to "Anomaly Detection" Section 5.3.2.  Trending and
   forecasting in the context of single-layer or multi-layer IP optical
   networks are pivotal components of predictive analytics, providing
   significant operational benefits through AINetOps.  In single-layer
   networks, such as purely IP or optical networks, trending involves
   analyzing historical data to identify patterns and behaviors over
   time.  For instance, in an IP network, trends in traffic volume,
   latency, and packet loss can be monitored to predict future network
   performance and capacity needs.  Similarly, in an optical network,
   trends in signal quality, attenuation, and equipment performance can
   be tracked.  By leveraging these trends, predictive models can
   forecast potential issues such as bandwidth bottlenecks or equipment
   degradation, allowing network operators to proactively optimize
   resources, plan for upgrades, and prevent service disruptions.

   In multi-layer IP optical networks, where both IP and optical layers
   interact, trending and forecasting become even more powerful.  This
   approach involves correlating data from both layers to gain a
   comprehensive understanding of network behavior.  For example, trends
   in optical signal impairments can be analyzed alongside IP traffic
   patterns to predict how physical layer issues might impact data
   transmission and overall network performance.  Forecasting in this
   multi-layer context can identify potential cross-layer issues, such
   as how an increase in optical signal noise might lead to higher IP
   packet error rates.  By anticipating these issues, network operators
   can implement preemptive measures, such as rerouting traffic or
   adjusting signal parameters, to maintain seamless service.  The
   integration of trending and forecasting through AINetOps thus enhances
   the resilience and efficiency of IP optical networks, ensuring
   superior performance and reliability.

### Predictive Maintenance

   Predictive maintenance in the context of single-layer or multi-layer
   IP optical networks is another aspect of predictive analytics, offering
   substantial operational benefits through AINetOps.  In single-layer
   networks, such as purely IP or optical networks, predictive
   maintenance involves using historical and real-time data to forecast
   when network components might fail or degrade.  For instance, in an
   IP network, data from routers and switches, such as CPU usage,
   temperature, and error rates, can be analyzed to predict hardware
   failures.  Similarly, in an optical network, monitoring parameters
   like signal strength, attenuation, and equipment performance helps
   predict when optical amplifiers or transceivers might need
   maintenance.  By accurately forecasting these maintenance needs,
   network operators can schedule interventions before failures occur,
   reducing unplanned downtime and extending the lifespan of network
   components.

   In multi-layer IP optical networks, predictive maintenance becomes
   even more effective by considering the interactions between the IP
   and optical layers.  This approach involves analyzing data from both
   layers to predict maintenance needs that could impact the entire
   network.  For example, if optical layer data indicates a gradual
   degradation in fiber quality, predictive models can assess how this
   might affect IP layer performance, such as increased packet loss or
   latency.  By understanding these cross-layer dependencies, network
   operators can prioritize maintenance activities that have the most
   significant impact on overall network health.  This proactive
   approach ensures that both layers of the network are maintained
   optimally, preventing cascading failures and maintaining high service
   quality.  Through the integration of predictive maintenance with
   AINetOps, IP optical networks can achieve greater reliability,
   efficiency, and cost-effectiveness, ensuring uninterrupted service
   delivery to end-users.

### Network Capacity Planning

   Predictive analytics also plays a crucial role in capacity planning
   and performance management.  By forecasting future traffic demands,
   network operators can ensure that the infrastructure is adequately
   scaled to meet those demands without over-provisioning.  This not
   only optimizes the use of resources but also ensures that the network
   can handle peak loads efficiently.  Additionally, predictive
   analytics can help in identifying and mitigating potential security
   threats by analyzing traffic patterns and detecting anomalies that
   may indicate malicious activities.

### Traffic Optimization

   Refer to Section 5.8 for details of AINetOps "Traffic
   Optimization".

   If "Traffic Optimization" is based on prediction of the traffic
   flows, it can be categorized as one of the areas of "Predictive
   Analytics".

## Network Operational Insights

   "Network Operational Insights" refers to the comprehensive visibility
   and understanding of an IP optical network's performance and
   behavior.  This concept involves collecting and analyzing detailed
   data about the network's operations.  By providing this valuable
   insight to network operators, they can gain a holistic view of the
   network's health and performance.  This enables operators to
   understand their network better and ensure a robust and resilient
   infrastructure.

   By having a detailed understanding of network usage patterns, traffic
   flows, and performance metrics, operators can make data-driven
   decisions to optimize resource allocation and improve overall
   efficiency.  This insight is particularly valuable in multi-layer IP/
   Optical networks, where the interplay between different network
   layers can be complex. {{!RFC5557}} provides examples of the PCE
   being used to optimize resource allocation.

   By leveraging these insights, operators can
   ensure that both the IP and optical layers are operating
   harmoniously, leading to optimal performance and cost efficiency.  In
   essence, Network Operational Insights empower operators with the
   knowledge needed to maintain a high-performing, resilient, and
   future-proof network infrastructure.

   The network operational insight can be grouped into two categories.
   By categorizing network operational insights into these two
   categories, operators can better prioritize their efforts and
   resources, ensuring both immediate and long-term network health and
   performance.

### Operational Insights Requiring No Further Analysis

   Network Operational Insights that fall under this category are those
   that can be obtained directly from existing data and real-time
   monitoring without the need for further analysis or simulation.
   These insights provide immediate, actionable information that can
   help network operators quickly identify and address issues.

   These insights are typically derived from real-time monitoring
   systems that continuously track network performance and health
   metrics.  For example, showing the Network Element (NE) with the
   highest alarms or displaying the current alarm table for a specific
   NE (e.g., NE 192.0.2.1) can provide immediate visibility into potential
   issues.  Similarly, identifying the NEs with the highest problems
   during the last hour or plotting the Bit Error Rate (BER) for the 10
   worst modems in a specific region (e.g., Northeast) allows operators
   to quickly pinpoint areas that require attention.  These insights are
   crucial for maintaining network stability and ensuring prompt
   resolution of emerging issues.

   These insights also include detailed information about network
   components and their performance.  For instance, identifying which
   photonic services cross a specific fiber (e.g., OTS1) or determining
   which modems are in use for a particular optical service (e.g., SVC-
   1) can help operators understand the current network configuration
   and its operational status.  Additionally, insights such as the
   average time to failure for similar equipment in the network or
   identifying geographic regions with higher rates of network issues
   provide valuable context for proactive maintenance and resource
   planning.  By leveraging these direct insights, operators can
   maintain a well-functioning network with minimal downtime and optimal
   performance.

### Operational Insights Requiring Further Analysis

   Network Operational Insights in this category require deeper analysis
   and possibly simulation to derive meaningful conclusions.  These
   insights often involve complex scenarios where simple monitoring data
   is insufficient, and further investigation is needed to understand
   the underlying causes or to predict future behavior.

   Insights that require investigation and simulation often involve
   predictive analytics and scenario planning.  For example, determining
   whether an L0 optical service can be created between two cities
   (e.g., city A and Y) involves analyzing the current network topology,
   available resources, and potential constraints.  Similarly,
   understanding why an IP TE-tunnel cannot be established between two
   points (e.g., point A and B) may require simulation of different
   routing scenarios and examination of network policies.  These
   investigations help operators to not only troubleshoot current issues
   but also to plan and optimize future network expansions and
   configurations.

   These insights are crucial for long-term network health and
   performance optimization.  Identifying the most common failure points
   in the network or detecting signs of degradation in wireless network
   performance requires a combination of historical data analysis and
   predictive modeling.  By simulating different maintenance activities
   based on current network health, operators can prioritize tasks that
   will have the most significant impact.  For instance, understanding
   what maintenance activities are needed based on the current network
   health can help in scheduling proactive maintenance that prevents
   future outages.  These insights enable operators to take a strategic
   approach to network management, ensuring sustained performance and
   reliability over time.

## Network Configuration Management

   AI can assist in automating the generation and enforcement of network
   configurations, significantly enhancing network reliability and
   performance.  By leveraging AI/Gen-AI algorithms, network operators
   can automate the creation of configuration templates that are
   precisely tailored to specific network requirements.  These templates
   can encompass a wide range of settings, such as Quality of Service
   (QoS) parameters, Access Control Lists (ACLs), tunnel configurations,
   and service configuration ensuring that each network segment is
   optimized for its intended purpose.  This automation not only speeds
   up the deployment process but also reduces the likelihood of human
   errors that can occur during manual configuration, leading to a more
   robust and efficient network infrastructure.

   Furthermore, AINetOps can play a role in validation of network
   configuration, i.e., "network configuration audit".  AINetOps plays a
   crucial role in validating configurations against predefined network
   configuration, ensuring that all network setups comply with intent
   configuration.  By continuously monitoring network configurations,
   AINetOps can detect and flag any deviations or misconfigurations that
   could pose security risks or operational inefficiencies.  For
   example, an AI system can identify inconsistencies in ACLs that might
   allow unauthorized access or detect suboptimal QoS settings that
   could degrade service quality.  By proactively addressing these
   issues, AINetOps helps maintain the integrity and performance of the
   network, enabling operators to focus on strategic initiatives rather
   than troubleshooting configuration errors.  This proactive approach
   to configuration management not only enhances network security and
   efficiency but also supports the dynamic and scalable nature of
   modern network environments.

## IP/Optical Multi-layer Planning

   Multi-layer planning is an approach that integrates the planning of
   IP and optical networks based on traffic patterns, network
   simulations, and capacity planning.  By analyzing these factors, IP
   optical networks can be designed to optimize resource allocation,
   enhance network efficiency, and ensure the network can handle current
   and future demands, resulting in a more resilient and scalable
   infrastructure.

## Cross-Layer and Multi-Layer Optimization

   AI can address the dependencies between different network layers,
   such as IP and optical layers, by integrating data and decision-
   making across these layers.  Multi-layer optimization algorithms
   ensure resource efficiency and performance by aligning the goals of
   individual layers, such as minimizing power consumption at the
   physical layer while maintaining SLA guarantees at the application
   layer.

   Moreover, Network Operational Insights facilitate informed decision-
   making for network optimization and capacity planning.  By having a
   detailed understanding of network usage patterns, traffic flows, and
   performance metrics, operators can make data-driven decisions to
   optimize resource allocation and improve overall efficiency.  This
   insight is particularly valuable in multi-layer IP/Optical networks,
   where the interplay between different network layers can be complex.
   By leveraging these insights, operators can ensure that both the IP
   and optical layers are operating harmoniously, leading to optimal
   performance and cost efficiency.  In essence, Network Operational
   Insights empower operators with the knowledge needed to maintain a
   high-performing, resilient, and future-proof network infrastructure.

## Traffic Optimization

   Another AINetOps operational benefit is "Traffic Optimization" where
   IP/Optical network traffic flows can be monitored and appropriate
   adjustments to network protocols, network topology, network
   configuration, load balancing, bandwidth allocation and so on can be
   dynamically initiated.  AINetOps traffic optimization considers
   multiple factors such as latency, packet loss, and link utilization,
   enabling networks to adapt to changing conditions in real time.

   Expanding on this, AINetOps traffic optimization leverages advanced
   algorithms to continuously monitor network conditions and predict
   potential congestion points before they impact service quality.  By
   analyzing historical data and real-time metrics, machine learning
   models can forecast traffic patterns and proactively adjust routing
   decisions to ensure optimal performance.  For instance, AINetOps can
   reroute traffic through less congested paths when high utilization is
   detected, balancing the load and enhancing overall network
   efficiency.  This intelligent management reduces latency and packet
   loss while maximizing bandwidth utilization.

   Furthermore, traffic optimization enhances the network's ability to
   respond to sudden changes in demand, such as peak usage times or
   unexpected traffic spikes.  Traditional static configurations may
   struggle with such fluctuations, leading to bottlenecks and degraded
   performance.  With AI, the network can dynamically reconfigure itself
   in real-time, redistributing traffic loads and reallocating bandwidth
   as needed.  This adaptability reduces the need for manual
   interventions and allows network operators to focus on strategic
   initiatives.  In essence, AI-driven traffic optimization enables
   networks to be more resilient, responsive, and capable of delivering
   consistent high-quality service.

   Note that the "Traffic Optimization" AINetOps operational benefit is
   closely related to "Predictive Analytics" covered in Section 5.3.

## Closed-Loop Automation

   Closed-loop automation systems use AI to adjust network
   configurations based on real-time data dynamically.  Reinforcement
   learning (RL) algorithms and policy-based decision frameworks can
   automate traffic engineering, resource allocation, and fault
   remediation tasks.  AI-driven systems ensure optimal network
   performance without human intervention by continually monitoring
   network state and applying corrective actions.

## Network Maintenance and Cleanup

   AI can automate cleanup operations by identifying and resolving
   transient issues, removing redundant configurations, and optimizing
   resource utilization.  These tasks may involve the identification of
   "stale" network states or unused resources, enabling networks to
   operate more efficiently.

## Network API Construction

   Another significant operational benefit of implementing AINetOps in
   single-layer or multi-layer IP/Optical networks is the generation of
   various Network Controller APIs.  These APIs are essential for the
   seamless integration of network controllers (whether IP, Optical, or
   multi-layer) with Operational Support Systems (OSS) or other network
   controllers.  A key advantage of this operational benefit is that
   operators do not need to possess in-depth knowledge of the APIs.
   Typically, network operators spend considerable time creating and
   verifying APIs to integrate IP or Optical network elements with the
   broader management layer, including OSS/BSS.  By developing robust
   and versatile APIs, network operators can ensure smooth communication
   and coordination between different network management systems,
   thereby enhancing overall network efficiency and performance.

   The APIs developed for network controllers serve as a bridge,
   enabling the OSS to interact with the underlying network
   infrastructure in a more dynamic and automated manner.  This
   integration allows for real-time data exchange, automated
   provisioning, and efficient fault management, which are essential for
   maintaining optimal network performance.  Moreover, these APIs
   facilitate the orchestration of network resources across different
   layers, whether it be IP or Optical, ensuring that the network can
   adapt to varying demands and conditions with minimal manual
   intervention.

   AINetOps leverages the power of Generative AI (Gen-AI) to further
   enhance this integration process.  By translating the operator's
   intent into precise network controller APIs, Gen-AI enables a more
   intuitive and user-friendly approach to network management.  This
   translation capability ensures that even complex operational
   requirements can be seamlessly converted into actionable commands for
   the network controllers.  This not only reduces the operational
   burden on network engineers but also significantly enhances the
   agility and responsiveness of the network to changing conditions and
   user demands.

## AI-Driven Security Monitoring

AI is becoming a cornerstone of modern network security, enabling
proactive, adaptive, and intelligent measures to safeguard network
operations against rapidly evolving threats. By leveraging AI, network
operators can enhance their ability to detect, prevent, and respond to
threats in real-time while automating complex     security processes.
This section details the key areas where AI drives security enhancements
in network operations.

### Threat Detection and Mitigation

AI significantly enhances threat detection and mitigation through ML and
deep learning. By analyzing vast amounts of network traffic data, AI
models identify unusual patterns and behaviors indicative of malicious
activity. This includes detecting anomalies that signal threats like
zero-day attacks or insider threats, generating real-time alerts, and
incorporating external threat intelligence to recognize known attack
signatures. Together, these capabilities enable faster response times and
improved threat recognition.

### Intrusion Detection and Prevention

AI improves intrusion detection systems (IDS) and intrusion prevention
systems (IPS) by enhancing accuracy and reducing false positives. It
achieves this through behavioral analysis, which identifies unauthorized
access or suspicious activities, and automated responses that isolate
compromised devices or block malicious IP addresses. Additionally, AI's
adaptive learning capabilities ensure continuous updates to address new
threats in dynamic environments.

### Security Policy Automation

Using AI would simplify the creation and enforcement of security policies
by automating configurations and adjustments, reducing the potential for
human error. It dynamically updates firewall rules and access controls
based on real-time threat intelligence, assigns risk scores to network
devices and applications to prioritize enforcement, and ensures
compliance with regulatory standards by monitoring for deviations and
recommending corrective actions.

## Multi-Agent Interworking

As seen in the use cases above, the usage of agents introduces various challenges,
spanning from the definition of APIs that can be used by the various agents to the
interworking with already existing components of the Network Management and Control stack.
New challenges arise when we move from a single agent to a multi-agent architecture.
When multiple agents are deployed we need to consider how they discover each other,
how they interwork with the discovered agents and how they are kept in sync.

The discovery aspect could be relatively simple in the short term, when few agents will
be deployed in the network and it could be possible to manually configure each agent
with the identifiers and capabilities of the other agents to interact with. With the evolution
of AI based architectures with more and more agents being part of the architecture,
mechanisms to advertise their presence and more importantly their capabilities will be required.

The second aspect to consider is the interworking between them. As of today, the way we
interact with agents is mostly based on LLMs, but would that be the best way for
interacting between them as well? Probably a more machine oriented type of language,
encoding and protocols would have better performance.

Note that agent discovery and inter-agent communication are the
subject of dedicated IETF activities: the DAWN (Discovery of Agents,
Workloads, and Named Entities) effort addresses the discovery of
agents and their capabilities, and the AGENTPROTO (Agent
Communication Protocols) effort addresses end-to-end protocols for
agent-to-agent communication.  Work on the discovery and interworking
aspects described in this section should be coordinated with those
activities, and with the GRASP-based rendezvous mechanism described
in {{?I-D.carpenter-anima-grasp-rendezvous}}.

## Human on the Loop

Human on the Loop has been integrated  into the AI-driven IP network
management and operation loop, providing closed loop safeguards for critical decisions and
enabling human-Agent collaboration (e.g., require human approval).

Interaction with the system is typically provided through natural language
interfaces that allow operators to review decisions, request explanations, and
provide guidance when necessary.

Implementation shall support conversational interaction via chat copilot
platforms (for natural language) and structured APIs (such as A2A-T, for
workflow based operations). It shall also maintain comprehensive trajectory
record or accountability logs of all human and Agent interactions to ensure
accountability, including intent submissions, approvals, and interventions.

Key interaction modes between Human operators and agents include:

• Intent Input (initiates the loop): Human operators submit high-level
  IP network intents (e.g., "deploy a low-latency L3VPN for 4G backhaul")
  via copilot or structured workflows.

• Decision Approval: The IP Network AI Agent escalates critical tasks
  (e.g., core route changes, bulk configuration deletions) via AI guardrail
  assitant to human operators for approval, providing context such as data
  simulation results and risk assessments.

• Intervention & Guidance: Human Operators intervene in ongoing tasks
  (e.g., correcting a fault diagnosis) or providing expert guidance
  (e.g., updating troubleshooting rules) to Agents.

• Feedback Provision: Human Operators submit feedback to AI guardrail
  assistant on Agent performance or misbehavior information  (e.g.,
  incorrect configuration suggestions) to drive continuous improvement.

Note that agent discovery and inter-agent communication are the
subject of dedicated IETF activities: the DAWN (Discovery of Agents,
Workloads, and Named Entities) effort addresses the discovery of
agents and their capabilities, and the AGENTPROTO (Agent
Communication Protocols) effort addresses end-to-end protocols for
agent-to-agent communication.  Work on the discovery and interworking
aspects described in this section should be coordinated with those
activities, and with the GRASP-based rendezvous mechanism described
in {{?I-D.carpenter-anima-grasp-rendezvous}}.

# AINetOps Scenarios and Use-cases

{Editor's note: This is a work in progress. More use cases will be added, and existing ones will be revised.}

This section further expands Section 5 by exploring scenarios and use cases for applying AINetOps in network
operations, focusing on their architectural, procedural, and protocol-level requirements.  Each use case
highlights how AINetOps can be leveraged to address challenges in network management and optimization, while
identifying the relevant IETF protocols, interfaces, and data models that are evolved or need enhancement.

For every use case described, the following dimensions are examined to provide a comprehensive understanding
of its implications and requirements.

* Architecture: The high-level architecture necessary to support the use case, including control-plane and
                data-plane interactions, as well as integration points for AI-driven systems.

* Interfaces and APIs: The key interfaces between AI systems and network elements, including management APIs
                        (e.g., NETCONF, RESTCONF, gNMI) and telemetry interfaces.

* Protocols: IETF protocols involved in enabling the use case, and potential extensions to existing protocols
             to accommodate AI-driven operations.

* Data Models: The data models required to represent network state, telemetry, policies, and configurations.

* Processes and Procedures: Workflow considerations for integrating AI systems into existing operational practices,
                            including training, validation, and deployment.

* Alignment with IETF Standards: Analysis of how existing IETF standards can be leveraged or extended to support the
                                 use case.

## Agentic AI-Driven Resilience Testing using AI Guardrail

This use case leverages AI to design and execute fault injection
scenarios that test the resilience of IP/optical networks under
simulated failure conditions.  By proactively introducing controlled
disruptions - such as packet drops, latency spikes, or optical signal
degradation- AI Guardrail system assesses the network Agent 's ability to detect, respond to,
and recover from faults. This approach enhances network robustness
by identifying weaknesses and validating automated recovery
mechanisms before real failures occur, addressing both single-layer
(IP or optical) and multi-layer (IP over optical) scenarios.

The Fault management AI Agent analyzes historical failure data (e.g., fiber cuts,
equipment outages), real-time network telemetry data (e.g., latency, BER), and
external factors (e.g., weather events, traffic surges) to model
probable failure risk points.  It then trigger AI Fault Inject Engine to
inject faults, monitors the network's response, and refines recovery
strategies, potentially in a closed-loop manner.  For example, an Fault management AI Agent
might predict a high-risk optical link based on trending attenuation, simulate a fiber
cut, and evaluate whether IP-layer rerouting maintains SLAs.  If
recovery is suboptimal, it suggests adjustments (e.g., updating TE
policies) and retests. And then Network Agent Behavior related to Tools Excution, Reason
can be collected and report to the AI Guardrail. The AI Guardrail can use Evaluate process
to Evaluate how well the Fault management Network Agent are run to support Network resilience test.

~~~~
            +--------------------------------------+
            |Network Management AI Guardrail       |
            |    +--------------+    +-----------+ |
            |    | Observability|(E) | Evaluation| |
            |    |    Process   +---->  Process  | |
            |    +---^----------+    +-----------+ |
            +--------|-----------------------------+
                 (D) |
               |----------------------------|
 +---------+   |      Fault Management      |
 |AI Fault |   |      Network Agent         |
 |Injection|   |----------------------------|
 | Engine  |         ^                |
 +----+----+     (B) |                | (C)
      |              |                v
      |  |-----------------------------------------|
      |  |  packet controller (P-PNC),             |
      |  |  optical controller (O-PNC),            |
      |  |  and/or higher layer controllers (MDSC) |
  (A) |  |-----------------------------------------|
      |                      ^
      |                  (B) |
      |                      |
  +---V---------------------------------------------------+
  |                                                       |
  |                    IP/Optical Network                 |
  |                                                       |
  +-------------------------------------------------------+

Legend
(A) Fault injection commands (e.g., disable link, drop packets, degrade signal)
(B) Telemetry feedback (e.g., latency, packet loss, BER)
(C)  Recovery actions (e.g., reroute traffic, adjust optical parameters)
(D) Agent Telemetry Collection (e.g., tool invoking success rate, Task Success rate)
(E) Agent Resilience Test Performance Evaluation

~~~~
{: #resilience-guardrail title="Agentic AI-Driven Resilience Testing using AI Guardrail" artwork-align="center"}

##  Network Active Assurance with Network AI Agent and AI Guardrail Support

   Network active and reactive assurance, both at the single- layer (IP
   or Optical) and multi-layer (IP over Optical), are critical
   components in maintaining the health and stability of modern IP,
   Optical, and IPoDWDM networks.  This process involves the
   identification and resolution of network issues as they arise,
   ensuring that any disruptions or degradations are promptly addressed.
   By employing AINetOps techniques, network engineers can quickly
   pinpoint the root cause of problems, whether they originate in the IP
   layer, the optical layer, or across both.  This reactive approach is
   essential for minimizing downtime and maintaining the quality of
   service expected by network users.

   In single-layer troubleshooting, the focus is on isolating and
   resolving issues within a specific layer of the network.  Multi-layer
   troubleshooting, on the other hand, requires a more integrated
   approach, as it involves identifying and resolving issues that span
   across multiple layers of the network.  This could include problems
   where an issue in the optical layer affects the IP layer.

   In active assurance, network faults have already occurred.  These
   faults may include impairments such as optical fiber
   cuts, IP packet drops, IP link latency issues, or Threshold Crossing
   Alarms (TCA), among others.

   As illustrated in Figure 3, active assurance assumes that a fault
   occurs in the IP/Optical network (Step A) and is subsequently
   detected automatically by higher-layer orchestrator (Step B). The
   orchestrator may employ detection methods that include monitoring
   alarms, analyzing performance telemetry data, or processing customer
   reports indicating service disruptions. To initiate troubleshooting,
   the detection logic launches the AIOps-Assistant, which serves as the
   front-end interface for AINetOps (Step C).  The assistant then sends
   a intent request and utilizes the backend assurance and troubleshooting
   mechanisms on the nework management agent to fullfill the intent,
   leveraging a Gen-AI multi-agent framework.  In Step D, a dynamic workflow
   is executed to diagnose the issue and identify potential root causes.  Optionally,
   at Step E, the Gen-AI dynamic workflow can recommend remedial actions
   to resolve the issue and implement these actions in a closed-loop fashion,
   ensuring automated network recovery. In Step F, the network controllers
   as Agent Fabric Gateway Collect log, trace, metric information on Agent
   behavior and report them to the Observabiltiy process to establish Agent behavior visibility.
   In step G, these information will be further fed into evaluation process
   to identify operational anomalies or performance drifts. In Step H,
   these operational anomalies and performance drifts will be captured
   by AI Guardrail Assistant, so that human operator can use captured information
   and AI Guardrial Assitant to check and validate user input,tools invocation,
   agent output, interrupt, and rollover from unanticipated behaviors in case of
   high risk operation.

~~~~
 +----------------------------+     +---------------+
 |  OSS/Service Orchestrator  |     | Human Operator|
 |      +---------------+     |     |               |
 |      |AIOps Asssitant|     |     +----^----+-----+
 |      +---------------+     |       (H)|    |(H)
 +---^------------------------+      +---|----V-----+
     |              |    +-----------|              |
     |              | (H)|  |--------| AI Guardrail |
     |              |Control|        +-----^--------+
     |              |Signal |              |Report
     |      Intent  |    |  |        +--------------+
     |     Request  |    | Intervene |   Agent      |
     |        (C)   |    |  |Signal  | Evaluation(G)|
     (B)            |    |  | (H)    |   Process    |
     |              |    |  |        +-----^--------+
     |              |    |  |              |Report
     |     +--------V----V--V-+      +-----|-------+
     |     |Network Management|  (F) |    Agent    |
     |     |     Agent (D)    +------>Observability|
     |     +--^-------|-------+      |   Process   |
     |        |       |              +-------------+
     |        |       |(E)  Observability
     |        |       |   Signal interface
  +--|--------|-------V-------+
  |           Network         |
  |         Controller        |
  +----------------^----------+
                   |(A)
 +-----------------|----------+
 |    Physical Network        |
 +----------------------------+


Legend:
(A) A fault happened in the network (e.g., Fiber cut, IP packet drop,
    TCA crossing etc.)
(B) The Network Controller and higher layer Orchestrator notifies Operator
(C) To start troubleshooting, AIOps-Assistant starts send service assurance intent request to Network Management Agent
(D) Network Management Agent starts troubleshooting using Gen-AI multi-agent dynamic workflow
(E) Optional remedial actions from Network Management Agent
(F) Telemetry for agent behavior visibility
(G) Evaluate operational anomalies or performance drifts
(H) The Agent management plane notifies Human Operator
(I) The human Operator uses AI guardrail Assistant to intervene or
    control Network Agent.
~~~~
{: #assurance-guardrail title=" Multi-layer Active Assurance Using Network Agent and AI Guardrail" artwork-align="center"}

## AI-Driven Policy Enforcement and Compliance evaluation using AI Guardrail

This use case leverages Network Change AI Agent to automate the enforcement of network policies and
evaluation of compliance with regulatory standards,ethical, and organizational boundaries and internal
guidelines. By continuously monitoring network Change AI Agent Behavior, AI Guardrail ensures that policies
are consistently applied and compliance requirements are met. This use case addresses both single-layer
(e.g., IP) and multi-layer (e.g., IP over optical) scenarios, as well as cross-domain environments.

The AI Guardrail system analyzes real-time telemetry (e.g., trace, logs, metrics, audit information),
historical data, and external inputs (e.g., regulatory updates, threat intelligence) to enforce
policies and evaluate compliance. For example, AI Guardrail can detect unauthorized changes to firewall
rules, enforce encryption standards for sensitive data, or ensure that network configurations align with
policy/compliance requirements such as GDPR requirements. If violations are detected, AI Guardrail can
automatically remediate issues or alert operators for manual intervention. In case of issue remediation
on high risk operation, the remdiation solution can be escalated to the human operator for approval.
AI Guardrails generally operate at three distinct operational levels to enforce policy and ensure :

- Input Guardrails (Prompt Shielding)

  - Goal: Detect and block malicious user behavior from the intent request before it reaches the network AI Agent.

  - Key Enforcements: Preventing prompt injections, filtering out Personally Identifiable Information (PII),
                      blocking hate speech, and stopping jailbreak attempts.

- Output Guardrails (Response Validation)

  - Goal: Verify that the generated configurations or policy is accurate, compliant, and safe for the end-user.

  - Key Enforcements: Preventing hallucinations (fact-checking against internal knowledge bases), blocking
                      toxic or biased outputs, and ensuring intellectual property (IP) compliance.

- Continuous Evaluation (Logging & Analytics)

  - Goal: Provide a transparent audit trail for compliance officers and regulators.

  - Key Enforcements: Maintaining detailed logs of inputs, safety violations, system interventions, and
                      Agent Behavior drift over time.

~~~~
                                   +---------------+
                                   | Human Operator|
                                   |               |
                                   +----^----+-----+
                                    (D) |    | (E)
                                    +---|----V-----+
                        +-----------|              |
                     (E)|  |--------| AI Guardrail |
                    Control|        +-----^--------+
                    Signal |              |Report
                        |  |        +--------------+
                        | Intervene |   Agent (C)  |
                        |  |Signal  | Evaluation   |
                        |  | (E)    |   Process    |
                        |  |        +-----^--------+
+-----------------------V--V-+            |Report
|                            |      +-----|-------+
|   Domain Specific Network  |      |    Agent    |
|       Change Agent         |------>Observability|
|    (Policy Enforcement     | (B)  |   Process   |
|       &Compliance)         |      +-------------+
+----------------------------+
             ^
             |(A)
             |
+------------V---------------+
|                            |
|  Packet Controller(P-PNC)  |
|  Optical Controller(O-PNC) |
|                            |
+----------------------------+
             ^
             |(A)
 +-----------V--------------+
 |    IP/Optical Network    |
 +--------------------------+

   Legend:
   (A) Network Change Agent Send Policy enforcement commands (e.g., block traffic, adjust QoS)
   (B) Agent Observability Information Feedback
   (C) Evaluate policy and authorization compliance
   (D) The Agent management plane notifies Human Operator about compliance reports and alerts
   (E) The human Operator uses AI guardrail Assistant to intervene or
    control Network Agent with the policy update.
~~~~
{: #audit-guardrail title="AI-Driven Policy Enforcement and Compliance Auditing using AI Guardrail" artwork-align="center"}

##   Network Anomaly Detection with AI Guardrail Support

   Network anomaly detection is a critical component of modern network
   security and management, aimed at identifying deviations from normal
   network behavior that may indicate potential threats or operational
   issues.  With the increasing complexity of networks and the growing
   sophistication of cyber threats, traditional rule-based detection
   methods are often insufficient.  The integration of machine learning techniques
   into network anomaly detection system offers a more
   dynamic and adaptive approach to detecting anomalies in real-time.
   The lifecycle of a network anomaly can be articulated in three
   stages, structured as a loop: Detection, Validation, Refinement.
   The Network Anomaly Detection stage is performed by the network anomaly
   detection Agent while Network Anomaly Validation and refinement is performed by Agent
   Observability module and AI Guardrail Assistant. The Network Anomaly
   Detection stage is about the continuous monitoring of the network
   through Network Telemetry {{?RFC9232}} and the identification of Symptoms.
   The key objective for the validation and refinement stage is clearly to decide if
   the detected Symptoms are signaling a real problem (a.k.a. requires
   action) or if they are to be treated as false positives (a.k.a.
   suppressing the alarm),perform detailed postmortem analysis of Problems
   with the objective to identify useful adjustments to the prevention and detection
   mechanisms.

   After the adjustments are generated, it will be sent to AI Guardrail
   Assistant and the AI Guardrail  Assistant apply adjustments to the Network
   Anomaly Detection Agent, the cycle starts again. Alternatively,  Any
   remediation action flagged as "high-impact" by the Network Anomaly Detection
   Agent is put into a correction queue and escalated to AI Guardrail Assistant,
   requiring manual administrative approval via an external management console
   before execution. If consecutive-point monitoring in the Agent Observability
   Module flags that the AI baseline has drifted or been poisoned by bad telemetry,
   the AI guardrail can switch the network back to traditional, static
   threshold-based detection.

~~~~
+----------------------------+
|     Agent Observability    |(D)Optimization
|+----------+   +----------+ |
||  Network |   | Network  | |       +------------+
||  Anomaly +---> Anomaly  |<+------->AI Guardrail|
||Validation|   |Refinement| |       | Assistant  |
|+-----^----+   +----------+ |       +----^-------+
+------+---------------------+            |
       |                                (E)Invention&
       |(C)Evaluation                     |  Control
       |  &Refinement    +----------------V--+
       +-----------------+                   |
                         |  Network Anomaly (B)Network Policy
           +-----------> |  Detection Agent  |-----------+
           | A)Network   |                   |           |
           | Telemetry   +-------------------+           |
           |                                             |
+----------+---------------------------------------------+--------+
| +--------|----------+       MCP Server      +----------|------+ |
| |                   |                       |                 | |
| |  Data Collection  |                       |    Response     | |
| |      Layer        |<------|       |-------|      Layer      | |
| |                   |       |       |       |                 | |
| +-------------------+       |       |       +-----------------+ |
+-----------------------------+-------+---------------------------+
            Southbound API    |       | Southbound API
 (NETCONF, IPFIX,BGP-LS, etc) |       v (NETCONF, PCEP, BGP, etc)
                      +-------------------+
                      |  Network Devices  |
                      | (Routers, Switches|
                      | Endpoints, etc.)  |
                      +-------------------+

Legend:
(A) Network Telemetry Information Collection
(B) Resolve the problem with the Network Policy
(C) Evaluate the network anomalies and identify useful adjustments
(D) Generate adjustments to the Network Anomaly Detection Agent
(E) AI Guardrail Assistant optimizes the Detection Agent based on
    Adjustment policy or Detection Agent requests Human-in-the-Loop
    Escalation from AI Guardrail Assistant

~~~~
{: #fault-guardrail title="Network anomaly detection optimization using AI Guardrail" artwork-align="center"}

# Agent Observability, Intervention, and Control

   The considerations in this section are cross-cutting: they apply to
   several of the operational benefits and use cases described in this
   document rather than constituting a single use case.  In particular,
   closed-loop automation (Section 5.9), the Gen-AI multi-agent dynamic
   workflows of Section 6.1 and Section 6.2, the multi-agent
   architectures of Section 6.15, and the agentic networks described in
   Section 6.16.3 all rely on increasing levels of agent autonomy.
   Because AI-native operations may be non-deterministic, network
   management agents can misbehave or deviate from expected behavior.
   Static AI guardrails, operating at the input/output or pre-action
   filter level, are insufficient for the full operational lifecycle:
   they often cannot detect, interrupt, or recover from unanticipated
   behaviors occurring at machine speed.

   This section therefore addresses the continuous observability of
   network management agent behavior, the ability of human operators to
   intervene when an agent goes wrong (e.g., task suspension, rollback
   to a last known safe state, or termination), and the control of what
   an agent is permitted to do before and during action execution.  The
   ICON effort is exploring the use cases, requirements, and
   solutions in this space; the key challenges identified include:

   *  Limited transparency in agent planning and decision-making.

   *  Difficulty attributing accountability to a specific agent entity
      or human.

   *  Lack of a standardized way to benchmark network management agents.

   *  Lack of human oversight of long-running autonomous workflows.

   *  Lack of rollback and termination commands, and of a bidirectional
      interaction channel between the human operator and the network
      management agent.

   The following aspects apply across the use cases identified above:

   *  Architecture

      Observability, evaluation, intervention, and control components
      attach to the agents introduced in the use cases above (e.g., the
      AIOps-Assistant front-end and the Gen-AI multi-agent dynamic
      workflows).  Agent behavior is captured as trajectory records:
      structured traces of the reasoning sequence, actions, and
      observations an agent follows to reach its conclusion.  A human
      oversight channel allows operators to monitor these records,
      inject policy, and take corrective action.

   *  Interfaces and APIs

      Two interoperability interfaces are identified: a telemetry
      interface carrying the traces, logs, and metrics that characterize
      agent behavior and operational state, and a human-agent
      interaction interface through which operators intervene in and
      control agent operation.

   *  Protocols

      Telemetry protocol extensions are needed for agent behavior
      observability.  Where possible, solutions should be built in a
      modular way using existing IETF protocols (e.g., NETCONF {{?RFC6241}}
      or RESTCONF {{?RFC8040}} for provisioning intervention and control
      policies), with protocol choices made only after the functional
      requirements have been agreed.  Coordination with the
      OpenTelemetry community is also anticipated.

   *  Data Models

      A common schema and information model for agent observability is a
      key gap: trace, log, and metric structures for agent behavior,
      trajectory records supporting auditability and accountability, and
      policy elements for intervention and for control.  Such models
      would complement the AI agent audit log and governance parameters
      proposed in {{?I-D.smith-opsawg-ai-network-governance}}.

   *  Processes and Procedures

      Human operators retain authority for monitoring, policy injection,
      emergency interruption, and corrective actions, consistent with
      the human-in-the-loop framework of {{?I-D.irtf-nmrg-llm-nm}}.
      Evaluation processes use trajectory records to assess how an agent
      solved a problem and whether it operated within its permitted
      boundaries.

   *  Alignment with IETF

      This work aligns with the ICON effort, discussed at an IETF
      126 side meeting, and with the AINETOPS mailing list activity
      described in Section 1.2.  Agent discovery, trust and
      authorization, and agent-to-agent communication are explicitly out
      of scope of ICON; those aspects are addressed by the DAWN and
      AGENTPROTO activities discussed in Section 5.13.

# Security Considerations

To be discussed in future versions of this document.

--- back

# IANA Considerations

This document has no IANA actions.

# Acknowledgments
{:numbered="false"}

This work has benefited from several discussions at the IETF and the
AI4NETWORK Side Meetings.

This work has benefited from several discussions at the IETF and the
AI4NETWORK Side Meetings.
