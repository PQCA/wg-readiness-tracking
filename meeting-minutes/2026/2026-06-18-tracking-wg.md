layout: default
title: 2026-06-18 Tracking WG Meeting Record
parent: 2026
grand_parent: Meeting Minutes
---

# Post-Quantum Cryptography Alliance - Readiness Tracking Working Group Meeting 18 June, 2026
[**View Recording**](https://zoom.us/rec/share/7FhIAbCXEWis8_rQZfa_LT5pF7UV7cDYyf180JR6hMxddNNim7v7W5Ph4ue9BCQ_.yPJIBkY0sf3gVpg2)
*Recordings are also available on your [Open Profile](https://openprofile.dev/my-meetings) page under Past Meetings*  
[**Join the meeting**](https://zoom-lfx.platform.linuxfoundation.org/meeting/92180236021?password%3Db0389cf7-46b4-4b12-8960-743736597cff&sa=D&source=calendar&ust=1779060340269221&usg=AOvVaw0xXXgXsS7I24ZkWvbZYInS)  
[**PQCA Meeting Calendar**](https://pqca.org/calendar/)  
[**Discord Server**](https://discord.pqca.org)

---

### **Antitrust Policy Notice**

Linux Foundation meetings involve participation by industry competitors, and it is the intention of the Linux Foundation to conduct all of its activities in
accordance with applicable antitrust and competition laws. It is therefore extremely important that attendees adhere to meeting agendas, and be aware of,
and not participate in, any activities that are prohibited under applicable US state, federal or foreign antitrust and competition laws. Examples of types
of actions that are prohibited at Linux Foundation meetings and in connection with Linux Foundation activities are described in the Linux Foundation
Antitrust Policy available at [linuxfoundation.org/antitrust-policy](https://linuxfoundation.org/antitrust-policy). If you have questions about these
matters, please contact your company counsel, or if you are a member of the Linux Foundation, feel free to contact Andrew Updegrove of the firm of Gesmer
Updegrove LLP, which provides legal counsel to the Linux Foundation.

---

## Attendance (_Alphabetical by 1st name_)
* [x] Aditya Koranga, NgKore \[TAC Chair\]
* [x] Aleksei Odinokov, PQC Ready
* [x] Andy Warner, Google \[Tracking WG Chair\]
* [] Avinash Nagadi
* [] Basil Hess, IBM
* [] Bill Turner, PKI Consortium
* [] Christian Pfister, LGT Bank
* [] Daniel Speciale, QInsight
* [] Guncha Malik, IBM
* [x] Hart Montgomery, Linux Foundation
* [x] Ian Palmer, GCIB
* [] Iyán Méndez Veiga, HSLU / ETH Zurich
* [x] Jane Ginn, Cyber Threat Intelligence Network
* [] Jeyaganesh Narayanaswamy, AIB (Ireland)
* [] Kyle Loree, Quantum Algorithms Institute
* [x] Marla Sumner, UT Austin
* [] Masab Iqbal, Multiverse Computing
* [x] Mike Novak
* [] Mukul Kulkarni, Technology Innovation Institute (Abu Dhabi)
* [] Neha Gupta, University of Surrey
* [] Salvatore Migliaccio, Namirial
* [] Shubham Kumar, NgKore
* [x] Sogo Pierre Sanon, Hydro Quebec Research Institute
* [x] Thomas Pöppelmann, Google

---
# Meeting Agenda

- **Overview of the WG**

 - **Goal**: Provide a reliable source of information about the Post-Quantum Cryptography readiness of common devices, libraies, operating systems and software via a community driven effort welcoming submission and updates from any interested party. To succeed, active community participation is needed. 
 - Approved by the TAC: https://github.com/PQCA/TAC/issues/139
 - Mailing List: https://lists.pqca.org/g/wg-readiness-tracking
 - GitHub Repository: https://github.com/PQCA/wg-readiness-tracking
 - Meeting Cadence: Every 2 weeks beginning May 21, 2026 [meeting link] - Open to the public

---

# Discussion & Updates

### **Introductions**

Have new attendees provide a quick intro (name, company / org, why they are interested in the Tracking WG)

* <pending>

---

### **Administrative**

  - Do we feel ready to shift to two person reviews or should we push that change out to August?
    - There was agreement to wait until August and re-evaluate 
  - Are there any vounteers to review the working group charter?
    - Aditya and Alecksi volunteered 

---

### **Review of open Issues and PRs**

  - [Open Issues](https://github.com/PQCA/wg-readiness-tracking/issues)
  - [Open PRs](https://github.com/PQCA/wg-readiness-tracking/pulls)
  - **<pending - ? were reviewed.>**

### **Open discussion**

  - Andy proposed reviewing HSM readiness at the next working group meeting
  - Aditya suggested that we standardize on "Not supported" and stop using "Not started"
    - There was agremeent to adopt this standard and Aditya volunteered to send a PR
  - Aditya raised the question of how we best reflect state when key encapsulation and signing are in different readiness states
    - We agreed on having seperate entries for each when they differ and merging them after both have been supported for a year with notes explaining when each one was ready. 
  - It was suggested that Network Devices and Semiconductors (including BIOS and TPMs) would be good next areas to explore
    - For network devices it will probably make sense to carve them up by vendor given the volume of devices
  -  There was brief discussion of whether tracking data sets and test tools made sense
    - There was agreement it may make sense in the future and such contributions would be accepted, but it is not an early priority for the WG. 

---

### **Next Steps / Action Items**

| Action Item | Owner | Status / Due Date |
|--------------|--------|------------------|
| Add contributions via PRs | All interested parties | Ongoing | 
| Review PRs | All interested parties | Ongoing | 
| Commit PRs we agreed on in the 2026-06-04 meeting | Andy Warner | Done |
| Send a reminder ~48 hours before future meetings | Andy Warner | Ongoing |
| Send a PR to add Aditya and Marla | Andy Warner | Done |

---

**Adjourned:** 09:29 am PT.
