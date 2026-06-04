layout: default
title: 2026-06-04 Tracking WG Meeting Record
parent: 2026
grand_parent: Meeting Minutes
---

# Post-Quantum Cryptography Alliance - Readiness Tracking Working Group Meeting 04 June, 2026
[**View Recording**](https://zoom.us/rec/play/FLek5nOMhDYuHjByzqfW-5gWiwz4XVN06txe6rkWQnptQf7AwiyDMaSLv5Ytcy5b5WUHmdrtLkH6DHsY.DsyJJBG8DDI91HG5?accessLevel=meeting&canPlayFromShare=true&from=share_recording_detail&continueMode=true&oldStyle=true&componentName=rec-play&originRequestUrl=https%3A%2F%2Fzoom.us%2Frec%2Fshare%2FGp_14Rj1NNbEsCmf47IoJAta64eDpOdADv8rTJPmawsuzS2pQ6JK9FOTzgQc7h1o.IDuoHCYOYyiD4Y51) 
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
* [X] Aditya Koranga, NgKore \[TAC Chair\]
* [X] Aleksei Odinokov, PQC Ready
* [X] Andy Warner, Google \[Tracking WG Chair\]
* [] Avinash Nagadi
* [] Basil Hess, IBM
* [] Bill Turner, PKI Consortium
* [] Christian Pfister, LGT Bank
* [] Daniel Speciale, QInsight
* [] Guncha Malik, IBM
* [X] Hart Montgomery, Linux Foundation
* [x] Ian Palmer, GCIB
* [X] Iyán Méndez Veiga, HSLU / ETH Zurich
* [X] Jane Ginn, Cyber Threat Intelligence Network
* [] Jeyaganesh Narayanaswamy, AIB (Ireland)
* [] Kyle Loree, Quantum Algorithms Institute
* [X] Marla Sumner, UT Austin
* [] Masab Iqbal, Multiverse Computing
* [x] Mike Novak
* [] Mukul Kulkarni, Technology Innovation Institute (Abu Dhabi)
* [X] Neha Gupta, University of Surrey
* [X] Salvatore Migliaccio, Namirial
* [] Shubham Kumar, NgKore
* [X] Sogo Pierre Sanon, Hydro Quebec Research Institute
* [] Thomas Pöppelmann, Google

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

* Ian and Mike introduced themselves.

---

### **Establishing Norms**

How do we want this WG to work?:

  - Mea culpa, I (Andy Warner) in my eagerness to get some contributions going I was not very rigorous reviewing some of the PRs that were contributed. Going forward, I think we should batch commits and only submit them during WG meetings. Reviews prior to meetings are strongly encouraged, but we will only commit non-adminsitrative / non-trivial changes in WG sessions.
    - **There was general consensus to proceed in this manner.**
  - How should we organize the information?
    - Areas to cover?
      - Proposed: Cryptography Libraries / Tools, Cloud Services, HSMs, Networking Devices, Operating Systems, Software **
        - **It was reiterated and agreed that we could focus on Cryptography Libraries and Tool, with an inclusive definition that would initially include various types of tokens and cryptographic primatives. There was consensus to use a second table on the cryptography.md page to seperate common libraries from everything else. We will not refuse or delay contributions in other areas, but the WG will continue to focus on core cryptography.**
    - Topic / file naming
    -   Proposed: Use reasonably generic signle words with names lower-cased. (e.g. cryptography.md. cloud.md, hsm.md, networking.md, os.md, software.md)
      -  **Not covered.**  
    - Do we want the same table format for all areas or should they be customized per tracked area?
      - **Consensus that we would have a standard for the leftmost columns in all tables, but different areas may add columns to the right if they are useful to better cover a particular area.**
  - Code commit rules
    - Proposed: Initially allow commits with a single approval by a second WG participant, but plan to move to requiring two approvals from reviewers representing different companies / orgs. at the start of Q3 2026.
      -  **General consensus to proceed in this manner.**
  - Individual entry requirements
    - Proposed: Keep the format as simple as possible. Only allow links to technical sources, not press releases or marketing materials.   
  - Who is interested in being added as a reviewer/committer?
    -  **Aditya and Marla volunteered.**

---

### **Review of open Issues and PRs**

  - [Open Issues](https://github.com/PQCA/wg-readiness-tracking/issues)
  - [Open PRs](https://github.com/PQCA/wg-readiness-tracking/pulls)
  - **All open items were reviewed.** 

---

### **Next Steps / Action Items**

| Action Item | Owner | Status / Due Date |
|--------------|--------|------------------|
| Add contributions via PRs | All interested parties | Ongoing | 
| Review PRs | All interested parties | Ongoing | 
| Commit PRs we agreed on in the 2026-06-04 meeting | Andy Warner | 2026-06-04 |
| Send a reminder ~48 hours before future meetings | Andy Warner | 2026-06-04 |
| Send a PR to add Aditya and Marla | Andy Warner | 2026-06-04 |

---

**Adjourned:** 09:29 am PT.
