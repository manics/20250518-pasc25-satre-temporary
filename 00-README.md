---
marp: true
paginate: true

# This requires html tags to be enabled
# VSCode: markdown.marp.enableHtml

style: |
  section.overlaybg h1,
  section.overlaybg ul,
  section.title h1,
  section.title h2,
  section.title h3 {
    background-color: rgba(205, 205, 205, .7);
    border-radius: 0.5em;
    padding: 0.2em 2em;
    margin: 0.25em 0;
  }
  section.overlaybg h1 {
    padding: 0.2em 0.5em;
  }
  section.overlaybg ul {
    padding: 0.2em 2em;
  }

  section.title h2,
  section.title h3 {
    text-align: right;
  }

  img[alt~="centre"] {
    display: block;
    margin: 0 auto;
  }

  img[alt~="float-right"] {
    float: right;
  }

  .box {
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: space-between;
  }

  .columns {
    display: flex;
    gap: 1rem;
  }

  .columns > div {
    /*flex: 1 1 0;*/
    flex: auto;
  }

  footer {
    position: absolute;
    left: 0;
    /* Full width is 1280, allow space for page number */
    width: 1220px;
    bottom: 0;
    height: 50px;
    text-align: right;
  }

  div.footer-logos {
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    text-align: left;
  }

  div.footer-logos img {
    height: 50px;
    display: inline-block;
  }

footer: |
  <div class="footer-logos"><img src="./hic-logo-h212-white.png"/></div>


---
<!--
_class: title
_footer: ''
-->
<style scoped>
  h3 {
    font-size: 30px;
    width: 500px;
    margin-left: 500px;
  }
  h3 img {
    vertical-align: middle;
  }
  div.footer-logos {
    height: 100px;
  }
  div.footer-logos img {
    height: 100px;
  }
</style>

# How Can a Standard Architecture for Trusted Research Environments Provide a Framework for HPC?
### Simon Li

---
# The Health Informatics Centre (HIC)

The vision:

![float-right w:200](raw/hic-chicken-tony.jpg)

> To advance data science and its community, simplifying access to sensitive data whilst maintaining security as a global leader in open, reproducible and scalable research platforms

https://www.dundee.ac.uk/hic

![bg fit right:35%](raw/hic-expertise.png)

TODO: More HIC/UoD images

<!--
Part of the School of Medicine, University of Dundee

Mission Statement: "To Innovate and enable world-leading data science research specialising in sensitive data"

- HIC supports high impact research through the collection and management of population based data
- We have expert teams in secure data management, governance, data engineering, research infrastructure, software, and business support
-->

---
# Purpose of this talk
- Explain what Trusted Research Environments (TREs) are
- Why existing HPC is not generally usable for TREs
- How we can start fixing that

---
# What are TREs and why do we need them?

TODO: Image

<!--
Example motivating case
-->

---
# Example: Can undiagnosed heart failure be detected from routine medical records?

[![bg right:35% fit vertical Echocardiogram](raw/heart-failure-risk-detected-ai-pioneering-study.webp)](https://www.dundee.ac.uk/stories/heart-failure-risk-detected-ai-pioneering-study)

<!-- Risk detected by AI in pioneering study -->

_Artificial Intelligence has the capability to detect people living with the risk of experiencing heart failure, new University of Dundee research has discovered._

https://www.dundee.ac.uk/stories/heart-failure-risk-detected-ai-pioneering-study

<!--
Heart failure: heart is unable to pump blood around the body effectively, gets worse over time
-->

---
![bg fit](raw/ehrs-ecgs-heartdisease.excalidraw.svg)

<!--
Echocardiography heart scans from heart failure patients
Electronic health records to identify heart failure patients with echocardiograms
AI used to extract measurements of hearts from echocardiograms, better than usual methods
Combined with test results from medical records

Patients from Scottish Health Research Register and Biobank (SHARE)
-->

---

---
## How can we give the research acess to the data?
- Can we give them a USB stick with all patient medical data to copy to their laptop?

TODO: Image

---
## NO! There are many reasons not to

[![drop-shadow:0,5px,10px,rgba(0,0,0,.4) w:800 centre](raw/northern-trains-lost-propertry.png)](https://media.northernrailway.co.uk/news/the-hamster-the-wig-and-the-cupboard-northern-customers-report-more-than-32-600-items-of-lost-property)

- So what can we do instead?

---
## We could minimise the data given to the researcher...
- Data minimisation: Only provide relevant fields from relevant records
- Pseudonymisation
- Use "synthetic" data

TODO: Image

---
<!--
_footer: https://securedatagroup.org/wp-content/uploads/2019/10/sdc-handbook-v1.0.pdf
-->

## ... and limit what they can publish

![h:500](raw/sdc-maps.png)

<!--
For example ensure only summary statistics can be published
-->
---
## We could accredit researchers to ensure they know their responsibilities...
- training courses on how to handle sensitive data
- understand why it's important to handle sensitive data in this way
- ensure that researchers are "trusted" before they can access patient data

TODO: Image

---
## ... along with reviewing what they plan to do
- Research projects in the healthcare field already go through ethics review
- is the proposed work in the public interest?
- does it include safeguards to protect patient data?

TODO: Image

---
## We could impose virtual or physical barriers on what they can do
- provide a locked-down compute environment with access to the data but no ability to copy data out
![centre](raw/computers-no-connection.drawio.svg)
- or only allow access to data from a physical location monitored with CCTV


![bg fit right:40%](raw/safepodbath02.png)

---
## In the UK these are embodied in the _"5 safes"_

We can balance how restrictive each of these _"safes"_ are to create a _"Trusted Research Environment"_

![bg right fit](raw/5-safes-circle.png)

---
# A researcher's view of a TRE

![](raw/tre-researchers-view.png)

---
# An example TRE

Virtual desktop environment (Windows or Linux), accessed via a web browser

---

![bg fit](raw/hic-tre-01.png)

---

![bg fit](raw/hic-tre-04.png)

---

![bg fit](raw/hic-tre-05.png)

---

![bg fit](raw/hic-tre-09.png)

---

# Why do we need a "standard" for TREs?

In the UK 50+ TREs have organically developed over the past 15+ years.
- Duplication of effort
- Most TREs were developed independently, making them harder to maintain
- Every TRE feels different to researchers, more time is wasted understanding how each TRE works
- No single TRE has all the data you want

TODO: Image

---
## Health is devolved to the 4 nations of the UK

![h:500 centre](raw/health-data-uk.png)

---
## The need for a coordinated approach has has been emphasised through several reports in the UK ...

![bg fit right](raw/goldacre-title-page.png)
![bg fit right:60%](raw/sudlow-review-cover.png)

---
## ... and across Europe
- [European Health Data Space Regulation (EHDS)](https://health.ec.europa.eu/ehealth-digital-health-and-care/european-health-data-space-regulation-ehds_en
)
  > a common framework for the use and exchange of electronic health data across the EU. It enhances individuals’ access to and control over their personal electronic health data, while also enabling certain data to be reused for public interest, policy support, and scientific research purposes.

TODO: Image

---
## Federated data analysis is unavoidable

TODO: Image


---
<style scoped>
  .columns div {
    border: 1px solid black;
    padding: 0.5em;
  }
</style>

# SATRE: Standard Architecture for Trusted Research Environments
### A guide on how to build and run a TRE

<div class="columns">

<div>

Four Architectural Principles:
- Usability
- Maintaining Public Trust
- Observability
- Standardisation

</div>

<div>

Four Pillars
- Information Governance
- Computing Technology
- Data Management
- Supporting Capabilities

</div>
</div>

TODO: Image

<!--
29 Capabilities
- 160 statements
  - 75 mandatory
-->

---
## Built by the UK TRE community
~60 organisations engaged
- 14 Collaboration Cafés
- 25 contributors making direct changes to the content

Public Involvement
- Workshops identified transparency as a key requirement
- Reflected in three (mandatory) statements

Version 1.0 Released Oct 2023

![bg right:40% fit](raw/uktre-swansea-2023.jpg)

---
## 4 pillars

![](raw/satre-pillars.drawio.svg)

<!--
1. Information governance
2. Computing technology and Information Security
3. Data management
4. Supporting Capabilities

It's not as easy as just securing your compute infrastructure
-->

---
<style scoped>
  td {
    font-size: 12pt;
  }
</style>

## Example capability: Network Management

|  | Statement | Guidance | Importance |
|---|---|---|---|
| 2.2.9. | Your TRE must control and manage all of its network infrastructure in order to protect information in systems and applications. | Network infrastructure must prevent unauthorised access to resources on the network. This may include firewalls, network segmentation, and restricting connections to the network. | Mandatory |
| 2.2.10. | Your TRE must not allow connectivity between users in different projects, or with access to different datasets. | Connectivity between users in the same project may be allowed,  for example to support shared network services within the project. | Mandatory |
| 2.2.11. | Your TRE must block outbound connections to the internet by default. | Limited outbound connectivity may be allowed for some services. | Mandatory |
| 2.2.12. | You should be able to monitor the network configuration of your TRE to check for misconfigurations and vulnerabilities. | This may include regular vulnerability scanning, and penetration testing. | Recommended |
| 2.2.13. | You should regularly monitor the network configuration of your TRE to check for misconfigurations and vulnerabilities. | This will involve following the monitoring procedure detailed above. | Recommended |

<!--
_footer: https://satre-specification.readthedocs.io/en/stable/pillars/computing_technology.html#network-management-application
-->

---
<!--
_footer: https://satre.uktre.org/en/evaluations/uod-hic/
-->

![bg fit](raw/satre-uod-evaluation-20231011-screenshot.png)

---
<style scoped>
  .center {
    text-align: center;
  }
</style>

## Who's using SATRE?

<div class="box">

![w:300](raw/sshn-network.png)

![w:300](raw/scwcsu-snsde-archi-model.png)

![w:300](raw/eosc-entrust-blueprint.png)

</div>

<div class="center">and several commercial providers</div>

<!--
NHS SDE
SSHN
EOSC-ENTRUST
Commercial providers
-->

---

## Not yet in SATRE: federation

SATRE is a common baseline for TRE, so now we can work on federation as part of
- DARE UK TREvolution (UK federated TREs)
- EOSC ENTRUST (European federated TREs)

---
# HPC: How is it used in TREs?
It mostly isn't

![bg fit right](raw/eo_circle_red_no-entry.svg)

<!--
https://commons.wikimedia.org/wiki/File:Eo_circle_red_no-entry.svg
-->
---
## Typical HPC has insufficient isolation for handling sensitive data
- Outbound network access: data can be copied out
- Shared drives: people can see each other's data
- Internal network connections: data can be passed between different internal projects
- Scratch space: data could be seen by others, or left behind on a node after a job completes

TODO: Image

---
## HPC information governance
- HPC administrators may not be trained in handling sensitive data
- A typical TRE will be audited/accredited, e.g. to ISO27001. HPC facilities may not be
- Is a TRE confident HPC administrators won't make mistakes in managing access?

TODO: Image

---
# The ultimate question
"Are the public happy with their sensitive data being analysed in shared HPC facilities?"

_(replace "public" with "data owner" for other data types, e.g. commercial)_

![bg right](raw/scotparliament-people.jpg)

---
# What can we do?
Note: "we" includes "you"!

- Build a shared understanding of how sensitive data differs from typical HPC datasets
- Understand the drivers behind the additional restrictions that TREs impose
- Think about what technical controls are practical in current and planned HPC facilities

TODO: Image

---
## New vs existing HPC
HPC facilities are expensive:
- Can new facilities include support for TREs? (Probably)
- How much of this can be retro-fitted to existing facilities?
  - (We definitely don't know yet)
- What is the performance penalty (and does it matter?)

![bg right](raw/building-site.jpg)

---
## A few starting points
This is a very active area of development, but a few areas of investigation include:
- ephemeral SLURM clusters in public cloud (SLURM nodes are ephemeral, never shared between users, storage always encrypted)

<div class="columns">
<div>

Shared HPC
![h:300 centre](raw/hpc-shared.png)

</div>
<div>

Multiple isolated HPC
![h:300 centre](raw/hpc-individual.png)

</div>
</div>

---
## A few starting points
- [FRIDGE (Federated Research Infrastructure by Data Governance Extension)](https://dareuk.org.uk/how-we-work/ongoing-activities/dare-uk-early-adopters/fridge/): treating a subset of HPC nodes as a TRE, and identifying what prerequisites the HPC provider must support
- Confidential computing: Zero-trust computing where even sysadmins can't access data
  - Trusted Execution Environments
  - Secure enclaves (AWS Nitro)
  - AMD SEV (Secure Encrypted Virtualization)
  - Intel Trust Domain Extensions (TDX))

TODO: Images

---
## NIST guidelines in progress

NIST have a couple of published and draft docs on securing HPC:
- [NIST SP 800-223](https://csrc.nist.gov/pubs/sp/800/223/final) High-Performance Computing Security: Architecture, Threat Analysis, and Security Posture
  - https://doi.org/10.6028/NIST.SP.800-223
- [NIST SP 800-234 Initial Public Draft](https://csrc.nist.gov/pubs/sp/800/234/ipd) High-Performance Computing (HPC) Security Overlay
  - https://doi.org/10.6028/NIST.SP.800-234.ipd

TODO: Images

---
## But don't forget, people are more important

There are limits to how "secure" your compute is


![Ken Thompson - Reflections on trusting trust](raw/reflections_on_trusting_trust.png)
https://doi.org/10.1145/358198.358210

---
# Thanks to...

TODO: Images

---
# Links for more information
- SATRE specification https://satre-specification.readthedocs.io/
- Public evaluations https://satre.uktre.org/
- DARE UK TREvolution https://dareuk.org.uk/how-we-work/ongoing-activities/trevolution/
- EOSC ENTRUST https://eosc-entrust.eu/


TODO: Insert QRCode to online slides
