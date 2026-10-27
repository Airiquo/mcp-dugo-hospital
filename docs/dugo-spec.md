                BULACAN STATE UNIVERSITY
COLLEGE OF INFORMATION AND COMMUNICATIONS TECHNOLOGY


       IT303: SYSTEMS ANALYSIS AND DESIGN
            PROJECT DOCUMENTATION


Project Title        Dugo +
                     Astrera, Rhez Stephen L.
                     Bansil, John Christian C.
Proponents           Cato, Iann Luigi Q.
                     Dimla, Justine B.
                     Sarmiento, John Paul S.

Course and Section   BSIT WMAD 3E-G2

Instructor           LILIBETH DG. ANTONIO, DIT

Institution          Bulacan State University

Submission Date      October 28, 2026



                              Academic Year [2026–2027]
TABLE OF CONTENTS
CHAPTER 1
PROJECT CONTEXT
1.1​Introduction
The Philippine Red Cross is the country's primary provider of voluntary blood services. Through its
National Blood Services Program, it collects, tests, processes, stores, and distributes safe blood and
blood products to hospitals and patients nationwide, and as of early 2023 it operated 31 blood
centers and 71 blood collection units (Philippine Information Agency, 2023). Its work follows the
National Blood Services Act (Republic Act No. 7719, 1994), which promotes voluntary,
non-remunerated blood donation. Beyond regular donation drives, it runs awareness campaigns and
works with government agencies, local government units, schools, private organizations, and
healthcare providers to keep the blood supply sufficient for routine medical needs and emergencies,
including surgeries, childbirth, trauma care, and cancer treatment.

Hospitals, blood banks, and local health offices still search for blood donors mostly by hand. When a
recipient needs blood, hospital staff determine the required blood type and go through donor records
that are commonly kept in paper files or spreadsheets (Eder, 2018). If no suitable donor is available
for an emergency transfusion, staff phone or text previous donors. Hospitals, relatives, and
community organizations sometimes post urgent requests on social media platforms such as
Facebook to reach potential donors (Philippine Information Agency, 2025). Blood bank personnel
and hospital coordinators then verify each donor's eligibility, confirm availability, and arrange the
donation schedule. The paperwork involved consists of donor registration forms, Recipient blood
request forms, blood inventory records, and donation history logs, and the tools are generally limited
to spreadsheets, mobile phones, SMS, email, and social media. With donor information spread
across multiple records and coordination done manually, identifying and contacting compatible
donors can take considerable time, particularly when a transfusion is needed immediately.

This manual process slows response time, puts recipients at risk, and cannot scale under the
pressure of a medical emergency. Because no single centralized public system exists, hospital staff
search paper logs and spreadsheets on their own while relatives rely on personal contact lists and
social media appeals, and confirming a donor's eligibility and availability takes considerable time.
When hospitals cannot secure enough supply, relatives are sometimes asked to source blood
themselves, a practice the Department of Health has flagged as risky: relatives have reportedly had
to transport and store the blood on their own, in some cases in home freezers, where it spoils
(Philippine Information Agency, 2025). Blood handled outside the standard collection-to-transfusion
chain also bypasses the typing and cross-matching safeguards meant to prevent mismatched
transfusions, which raises the risk of a transfusion reaction (A.D.A.M. Medical Encyclopedia, 2025).
Part of the shortage is a donor-pool problem as well. The Department of Health says at least one
percent of the population needs to donate to keep the supply sufficient (SunStar Cebu, 2026), yet a
study of Metro Manila adults describes donation practice in the Philippines as low despite recruitment
efforts (Mappala et al., 2023). Without a way to track and re-engage willing donors, the pool stays
inactive and every new request starts the search from zero.

Donor records are scattered across non-centralized spreadsheets and paper logs, which makes
monthly reporting and data retrieval slow and error-prone. The problem is well documented: the
Philippine Red Cross built its own Online Blood Bank Management Information System to address it
(Eder, 2018). The disorganization creates a data privacy concern as well. Donor information typically
includes blood type, contact details, and health history, which counts as sensitive personal
information under the Data Privacy Act of 2012 (Republic Act No. 10173) and its health-sector
implementing guidelines (Department of Health, 2020). Both require such data to be securely stored,
access-controlled, and processed only with proper consent (Respicio & Co., 2025), a standard that
paper logs and informal spreadsheets are not designed to meet.

The proposed system addresses these gaps by digitizing donor records into a centralized,
searchable database of structured donor profiles that include blood type, current location, and
donation history, so records can be retrieved instantly. It automates the search for compatible donors
and sends and in app and email match alerts, removing the delay of manual coordination so that
recipients receive aid sooner. The donor-facing mobile web app and the web platform for hospital,
blood bank, and administrative users share a single workflow, from request submission to donor
matching to confirmed donation, so hospitals, blood banks, and donors all work from the same
real-time data. To keep that workflow transparent, the system records key transactions (requests,
matches, confirmed donations, and reward points) in a blockchain transaction log. Each record
carries a cryptographic hash of the record before it, so tampering with an earlier record can be
detected. Existing blood donor management systems have been criticized for lacking a reliable audit
trail and traceability, which blockchain-based designs have been proposed to address (Sadri et al.,
2021). The hash-chained log applies the same chaining idea in a lighter form and gives hospitals,
blood banks, and administrators a verifiable record of what happened and when.

Dugo+ is a Transaction Processing System designed to handle time-critical, high-volume
donor-matching transactions accurately and immediately. It targets three friction points of the current
manual process: slow donor identification, delayed treatment, and an inactive donor pool. The
system serves four types of users: blood donors; Recipients or their family members who need
blood; hospital or blood bank staff who coordinate donations; and system administrators who
manage user accounts, system records, and the audit trail. Donors register and keep a profile
containing their blood type, location, and donation history. When a hospital submits an urgent blood
request, or a recipient's relative submits one that hospital staff then verify, the system automatically
searches the donor records for people who match in blood type, are eligible to donate, and are
located nearby. Once its GPS-based matching engine finds a match, Dugo+ immediately sends an
app and email notification to both the donor and the requesting hospital. A matched donor who
agrees to donate does so through the hospital or blood bank's standard collection, screening, and
testing process, so Dugo+ speeds up the search for donors without bypassing those safeguards.
Together, these functions aim to make donor coordination faster and more dependable.



1.2​Objectives
General Objective
To develop and design a real-time blood donor matching and emergency request system,
composed of a mobile web application and a web platform, for hospitals and blood banks, including
those of the Philippine Red Cross.

Specific Objectives

        No.                                       Specific Objective
   1            To Develop a centralized donor database that stores donor profiles and
                donation history
2   To Develop a mobile web application for donors and Recipients

3   To Implement a notification system for emergency blood donation requests

4   To Develop a location-based compatible donor matching engine that
    searches within a tiered radius of an incoming blood request.

5   To Evaluate the system using black box testing,
   1.3​Scope



   1.4​Limitations

Dugo+ coordinates donors and requests; it does not replace medical judgment. Its eligibility checks rely on
recorded donation history and on what donors report about themselves, so final screening, typing,
cross-matching, and infectious disease testing remain with licensed blood bank personnel. The system also
does not cover blood collection, transport, storage, or transfusion, and it cannot guarantee that a matched
donor will respond or that blood will be available in time. Donation stays voluntary. Requests from recipients
or relatives are verified by hospital staff before donors are alerted, so verification depends on staff being
available and can add delay, and the system cannot itself tell a genuine request from a false one.

Matching quality depends on the location data behind it. Smartphone GPS is typically accurate to within
about 4.9 meters under open sky, but accuracy worsens near buildings, bridges, and trees (GPS.gov,
2022). Donors must also allow location access and keep their profile updated. Email delivery depend on
third-party gateways and network conditions, so the response-time target applies to when the system sends
notifications, not to when they arrive, and the system needs an internet connection. The pool is limited too:
the system can only find donors who have already registered, and blood inventory is encoded manually by
staff rather than linked to laboratory equipment or existing hospital and Red Cross information systems.

Because the transaction log is a hash-chained table in the system's own database with no distributed
consensus, it can show that a record was altered but cannot stop someone with full database access from
rebuilding the chain, so detection holds only while the chain is intact. It also cannot verify that an event
actually happened outside the system. To respect donors' privacy rights, the log stores only references and
hashes, not personal information, so records can still be corrected or deleted in the main database.
Registering with the National Privacy Commission, which applies to organizations processing sensitive
personal information of 1,000 or more individuals (National Privacy Commission, n.d.), and other formal
data privacy steps belong to whichever organization eventually operates the system.

The rewards feature is limited to small-value vouchers and recognition. Small tokens and refreshments are
compatible with voluntary, non-remunerated donations, but payment in cash or in kind that could substitute
for money is not (World Health Organization, 2010). Partner sponsorship is voluntary, each voucher has a
small maximum value, and points cannot be converted to cash or traded. Points are awarded only after staff
confirm a completed donation, in keeping with the humanitarian principle of the National Blood Services Act
(Republic Act No. 7719, 1994).

Finally, the system is evaluated through black box testing only. This shows that the functions behave as
specified, but not code-level quality, performance under heavy load, or the real-world effect on donor
turnout and response time. Testing uses simulated data, meaning generated donor profiles and requests,
not real donor records, and involves 2 testers for each user role. The app is available in English only for
now, and the prototype is tested in a single setting, Bulacan Medical Center, not deployed nationwide.
   1.5​Significance of the Study
Recipients and their families. In an urgent request, the time spent searching for a donor is time the
Recipient spends waiting. Dugo+ shortens that search by querying the donor pool automatically, so
families no longer depend on calls and social media posts. It also eases the pressure on relatives to find
blood on their own, a practice the Department of Health has flagged as risky (Philippine Information
Agency, 2025). The World Health Organization (2010) notes that this pressure falls on families already
under stress from the patient's illness.

Donors. Donors get one place to see their profile and donation history, and they are alerted only when a
request fits their blood type, eligibility, and location. This matters because a study of Metro Manila
adults found that respondents knew least about the interval between successive donations (Mappala et
al., 2023). The same study identifies younger people as promising donors to recruit and retain. A pilot
survey of U.S. adults aged 18 to 39 found that about 73% were willing to use an app to track their blood
donations (Li et al., 2023), which suggests a readiness worth testing among Filipino donors. Repeat
donors also receive recognition through the rewards feature.

Hospitals and blood banks. Staff work from a single searchable record, which addresses the slow,
error-prone retrieval and reporting problem described by Eder (2018). The inventory feature and
request-tracking dashboard show what is on hand and who has responded.

The Philippine Red Cross and the DOH. A searchable, eligibility-aware pool of willing donors supports
the DOH goal of widening the donor base and the voluntary donation mandate of Republic Act No.
7719.

Administrators and oversight. Because requests, matches, donations, and point awards are logged in a
tamper-evident record, administrators and partner institutions can trace what happened in any
transaction, which spreadsheets and paper logs do not allow. The chained-hash approach borrows from
blockchain-based designs proposed for the same traceability reasons (Sadri et al., 2021), in a form light
enough for a single-hospital prototype.

Reach. About 98 million Filipinos were online by the end of 2025, and mobile connections were equal
to 117 percent of the population (DataReportal, 2025). That makes a mobile-first solution realistic, and
SMS alerts still reach donors whose connections do not include data.

Future researchers and developers. The largest share of the apps and studies reviewed by Li et al.
(2023) focus on finding donors and blood centers (44.1%), while only 8.8% address retaining donors.
Dugo+ gives later studies a documented, working baseline to extend, for example with a live pilot
deployment.
CHAPTER 2
SYSTEMS ANALYSIS AND DESIGN
This chapter translates the documented problem into validated requirements, improved business
processes, data and behavior models, and a technical design for the proposed system.


2.1​Requirements Analysis
2.1.1​Functional Requirements

Account Management (Donor & Recipient) Requirements

    ID                                          Functional Requirement
 FR-01    The system shall allow Donors and Recipients to register an account by providing personal
          details, blood type, and contact information, with email verification through a confirmation link.


 FR-02    The system shall allow Donors and Recipients to log in using their registered credentials and
          maintain a secure session.


 FR-03    The system shall allow Donors and Recipients to log out of their accounts, ending the active
          session securely.


 FR-04    The system shall allow Donors and Recipients to create and edit a profile containing
          blood type, location, date of birth, and eligibility information.




Donor Requirements

    ID                                          Functional Requirement
 FR-005 The system shall allow Donors to view a list of available blood requests filtered by blood
        type compatibility and proximity, using the tiered search radius defined in NFR-05.
 FR-006 The system shall allow Donors to accept or decline a blood request, updating the
        request status in real time.
 FR-007 The system shall send emergency notifications to Donors email when a compatible and
        eligible match is found nearby.
 FR-008 The system shall allow Donors to track their donation history, including dates, locations,
        and hospitals or blood banks involved.
 FR-009 The system shall allow Donors to view accumulated points and rewards earned from
        completed donations.
 FR-010 The system shall allow Donors to view a health tracker showing donation eligibility
        status and recommended next donation date.
 FR-023 The system shall display the precise geolocation of all hospitals within donor radius on
        the map.
 FR-024 The system shall prevent a donor from registering for a new Whole Blood Donation until
        56 days (8 weeks) have elapsed since their last Whole Blood Donation.
 FR-025 The system shall prevent a donor from registering for a new Platelet Donation until 7
        days have elapsed since their last Platelet Donation.
 FR-026 The system shall prevent a donor from registering for a new Plasma Donation until 28
        days have elapsed since their last Plasma Donation.
 FR-027 The system shall prevent a donor from registering for a new Double Red Cell Donation
        until 112 days (16 weeks) have elapsed since their last Double Red Cell Donation.
 FR-028 The system shall display the relevant donation eligibility guidelines (e.g., recent surgery,
        transfusion, tattoo/piercing, pregnancy) to the donor based on their selected donation
        type before they can accept a blood request.
 FR-029 The system shall require the donor to check an acknowledgment box confirming they
        have read and meet the displayed eligibility guidelines before they can accept a blood
        request.
 FR-030 The system shall record the date and time of the donor's guideline acknowledgment as
        part of the donor's request history.
 FR-036 The system shall automatically award reward points to a Donor's account once Hospital
        staff confirm a completed donation, per FR-033.
 FR-038 The system shall obtain and record a Donor's consent, at registration or at match time,
        before their profile information is shared with or accessed by a Hospital, per NFR-16.


Recipient Requirements

    ID                                      Functional Requirement
 FR-011 The system shall allow Recipients to submit a blood request specifying blood type,
        quantity, urgency level, and hospital location.

Hospital Requirements

    ID                                      Functional Requirement
 FR-012 The system shall allow Hospital staff to log in and log out using role-based hospital
        credentials.
 FR-013 The system shall allow Hospital staff to edit and maintain the hospital's profile
        information.
 FR-014 The system shall allow Hospital staff to view the total number of blood units collected
        over a selected period.
 FR-015 The system shall allow Hospital staff to view the hospital's location on a map for donor
        navigation purposes.
 FR-016 The system shall allow Hospital staff to view a list of currently active blood requests
        submitted within their facility.
 FR-017 The system shall allow Hospital staff to create blood requests on behalf of Recipients
        and route them to matching donors.
 FR-018 The system shall allow Hospital staff to manage the hospital's subscription plan for
        continued system access.
 FR-020 The system shall allow hospital staff to check current blood inventory levels and view
        the hospital's blood donation history.
 FR-021 The system shall allow hospitals to submit emergency blood donation requests based
        on blood type compatibility and proximity, using the tiered search radius defined in
        NFR-05.
 FR-031 The system shall route all matched donors to the hospital for final eligibility verification
        (physical screening, blood tests, and medical history check) prior to the actual donation.
 FR-032 The system shall allow Hospital staff to mark a matched donor's status as "Cleared,"
        "Deferred," or "Rejected" after conducting their own eligibility screening.
 FR-033 The system shall update the donor's donation history only after Hospital staff confirms a
        completed donation, ensuring FR-024–FR-027 intervals are based on verified data, not
        self-reported claims.
 FR-034 The system shall allow Hospital staff to add or update blood inventory records after a
        completed donation or issued transfusion.



System Administration Requirements

    ID                                      Functional Requirement
 FR-040 The system shall allow System Admin to create Hospital accounts and to suspend or
        remove Hospital and Donor/Recipient accounts as needed. Donor and Recipient
        accounts shall continue to be created via self-registration per FR-001.
 FR-041 The system shall allow System Admin to configure system-wide parameters, including
        the tiered matching radius defined in NFR-05 and notification retry settings.
 FR-046 The system shall allow System Admin to log in and log out using role-based
        administrator credentials.
 FR-047 The system shall allow System Admin to view their own account profile.


System Wide/Cross Cutting Requirements

    ID                                      Functional Requirement
 FR-019 The system shall secure donor and recipient information by enforcing access controls
        and encryption in compliance with the Data Privacy Act of 2012 (RA 10173).
 FR-022 The system shall display the precise geolocation of donors and recipients after having a
        match.
 FR-035 The system shall allow authorized users (Admin/Hospital) to view the blockchain-based
        transaction/audit log of donation records and data access events, as maintained per
        NFR-15.
 FR-037 The system shall prioritize higher-urgency blood requests, as specified in FR-011,
        FR-017, and FR-021, ahead of lower-urgency requests in the donor matching queue
        and the Hospital dashboard's request list.
 FR-039 The system shall allow Donors and Recipients to submit a request to access, correct, or
        delete their personal data, and allow System Admin to process such requests, per
        NFR-19.
 FR-042 The system shall commit a new blockchain record for every donation confirmation,
        inventory update, and data-access event, recorded at the time the action occurs.
 FR-043 The system shall prevent modification or deletion of committed blockchain records; any
        correction shall be recorded as a new linked entry rather than an edit.
 FR-044 The system shall allow System Admin to verify that a given audit record has not been
        altered by checking its hash against the chain.
  FR-045 The system shall store only hashed or non-identifying references to personal data within
         blockchain audit records, ensuring that donor and recipient data deletion requests
         (FR-039) can be fulfilled without compromising blockchain record immutability (FR-043).
  FR-048 The system shall allow Donors, Recipients, and Hospital staff to reset their password
         and recover account access through a verified channel (e.g. registered email). System
         Admin accounts are excluded, as they are premade and managed directly by the
         development team.

2.1.4 Non-Functional Requirements
Non-functional requirements describe how well the system must operate. Avoid vague
statements such as “fast,” “secure,” or “user-friendly”; use measurable acceptance criteria
whenever possible.

     ID          Category                         Non-Functional Requirement
  NFR-01     Performance     The system shall match a submitted blood request with eligible
                             nearby donors within 3 seconds of submission.
  NFR-02     Performance     The system shall send an in app and email notifications to matched
                             donors within 3 seconds of a match being found.
  NFR-03     Performance     The system shall support at least 500 concurrent users without
                             noticeable performance degradation.
  NFR-04     Performance     The system shall load the donor dashboard, request list, and
                             hospital dashboard within 3 seconds under normal network
                             conditions.
  NFR-05     Performance     The system's GPS-based matching engine shall process a search
                             query matching donors to nearby blood requests and blood
                             requests to nearby donors using a tiered search radius (starting at 5
                             km, expanding to 10 km, then 15 km, and capped at 20-25 km if no
                             match is found), completing the search in under 5 seconds.
  NFR-06     Reliability     The system shall be available 99.5% of the time to support blood
                             requests occurring at any hour, including emergencies.
  NFR-07     Reliability     The system shall retain a blood request as active and retry
                             notification delivery if the initial alert and email fails.
  NFR-08a Reliability        The system shall perform automated backups of all donor, recipient,
                             and hospital data to cloud storage to prevent data loss in the event
                             of a server failure.
  NFR-08b Reliability        The system shall perform full data backups at least once every 24
                             hours, with active blood requests and match transactions backed up
                             in real time.
  NFR-09     Reliability     The system shall gracefully handle third-party service outages
                             (email, GPS) and inform the user when a dependent service is
                             unavailable.
  NFR-10     Security        The system shall encrypt all sensitive personal and health-related
                             data both at rest and in transit.
  NFR-11     Security        The system shall restrict access to donor information to authorized
                             hospital users and System Admin only, verified through role-based
                             access control.
  NFR-12     Security        The system shall require email verification for account registration to
                             prevent fake or duplicate accounts.
  NFR-13      Security          The system shall enforce a minimum password length and
                                complexity requirement of at least 8 characters.
  NFR-14​     Security          The system shall automatically end a user session after a defined
  (DEFFE                        period of inactivity.
  RED)
  NFR-15      Security          The system shall maintain a tamper-evident blockchain-based audit
                                trail of donation records, inventory updates, and donor information
                                access.
  NFR-16      Security          The system shall obtain and record donor consent before donor
                                information is shared with or accessed by a hospital.
  NFR-17      Compliance        The system shall comply with the Data Privacy Act of 2012
                                (Republic Act No. 10173) in the collection, storage, and processing
                                of personal data.
  NFR-18      Compliance        The system shall comply with DOH Administrative Order No.
                                2020-0030 on data privacy guidelines for health information.
  NFR-19      Compliance        The system shall provide a mechanism for users to request access
                                to, correction of, or deletion of their personal data.
  NFR-20      Usability         The system's mobile web app interface shall be simple and intuitive
                                for first-time users with minimal technical literacy.
  NFR-21      Usability         The system shall display clear, immediate error messages in plain
                                language.
  NFR-22      Usability         The system shall support use in low-connectivity conditions, with
                                clear messaging when internet-dependent features are unavailable.
  NFR-23      Usability         The Hospital dashboard shall present request status, inventory, and
                                donor matches in a clear, scannable layout for time-pressured staff.
  NFR-24      Scalability       The system's architecture shall support future expansion to
                                additional hospitals and geographic areas without redesigning the
                                core matching engine.
  NFR-25      Scalability       The centralized donor database shall accommodate a growing
                                number of donor profiles and records without significant
                                performance loss.
  NFR-26      Maintainability   The system shall use a modular architecture allowing individual
                                features to be updated independently.
  NFR-27      Maintainability   The system shall log system errors and exceptions to support
                                debugging and maintenance.
  NFR-28      Compatibility     Donor and Recipient access shall be via Android/iOS mobile web
                                app.
  NFR-29      Compatibility     Hospital and System Admin access shall be via a web
                                browser-based dashboard.



2.2​Business Process Analysis
Student guidance: Examine how work is currently performed before deciding what to automate. Document
actors, steps, inputs, outputs, rules, delays, errors, duplication, and control points. Present both the
existing AS IS process and the improved TO BE process.
2.2.1​Existing AS IS Process
[ Describe the current process from start to finish. Explain who performs each activity, what
information or document is used, and how the process ends. ]



 Step     Responsible          Input                Activity          Output            Problem or
             Actor                                                                      Bottleneck
                                                                                   Request information
 1      Recipient /        Blood          Recipient or            Blood request
                                                                                   may be incomplete
        Hospital Staff     requirement    hospital staff          information
                                          identifies the                           or require manual
                                          need for blood                           coordination.
                                          and gathers the
                                          required blood
                                          type, quantity,
                                          and hospital
                                          information.
 2      Recipient /        Blood request The blood                Blood request    Communication may
        Hospital Staff     information   request is               communicated     be slow, especially
                                         communicated to                           during urgent
                                         available                                 situations.
                                         contacts, donors,
                                         or other sources.
 3      Hospital Staff /   Required blood Hospital staff or       List of potential Donor information is
        Blood              type and donor blood                   donors            scattered across
        Coordinator        records        coordinators                              multiple records,
                                          search paper                              making compatible
                                          files,                                    donors difficult and
                                          spreadsheets, or                          time-consuming to
                                          existing donor                            identify.
                                          records for
                                          potential donors
                                          with the required
                                          blood type.
 4      Hospital Staff /   Donor contact Potential donors         Donor            Contacting multiple
        Blood              information   are contacted            response         donors through
        Coordinator                      through phone                             separate
                                         calls,email, or                           communication
                                         social media and                          channels can cause
                                         asked about their                         delays.
                                         availability to
                                         donate.
 5      Donor              Blood request The donor                Accepted or      Donor responses may
                                         decides whether          declined         not be received
                                         they are                 response         immediately.
                                         available and
                                         willing to respond
                                         to the blood
                                         request.
6    Hospital Staff     Donor          Hospital staff       Donor            Coordination depends
                        information    coordinate with      scheduled for    on manual
                                       an available         screening        communication.
                                       donor and
                                       provide
                                       instructions for
                                       reporting to the
                                       hospital.
7    Hospital Staff     Donor personal Hospital staff       Cleared,         Eligibility verification
                        and medical    conduct physical     deferred, or     occurs only after the
                        information    screening, blood     rejected donor   donor reaches the
                                       testing, and                          hospital.
                                       medical history
                                       checking to
                                       determine donor
                                       eligibility.
8    Donor / Hospital   Cleared donor The donor             Completed        Donation information
     Staff                            proceeds with         donation         requires manual
                                      the blood                              recording and
                                      donation at the                        updating.
                                      hospital.
9    Hospital Staff     Donation       Hospital staff       Updated          Manual record
                        information    record the           donation and     updates can cause
                                       completed            inventory        delays or inaccurate
                                       donation and         records          records.
                                       update the
                                       hospital's blood
                                       inventory.
10   Hospital Staff     Donation       Hospital staff       Donation         Maintaining accurate
                        record         retain the           history          historical records is
                                       donation                              difficult when records
                                       information for                       are manually
                                       future reference,                     managed.
                                       including the
                                       donor's previous
                                       donation activity.
                             Figure 2.1. Existing AS IS Business Process




2.3​Data Flow Diagram and Context Diagram
Student guidance: Show how data moves among external entities, processes, and data stores. Start with
a context diagram containing one process for the entire system, then decompose it into Level 0 and
lower-level DFDs as needed. Balance inputs and outputs between levels. Do not show program control
flow.

   Symbol or Element                                  Project-Specific Meaning
  External entity          Donor, Recipient, and Hospital staff

  Process                 Manage Account, Submit Request, Match Donor, Manage Inventory, ​
                          Send Notification


  Data flow                Profile, Request Acceptance, Emergency Blood Request Notification, Blood
                           Request, Status Update, Request, Matches, Donor Data, Request data, Match
                           found , Clearance Status, Hospital Request, Request Info, Donor Profile,
                           Compatible donors, Nearby donors, Eligible donors, Match Record

  Data store               D1 Donor DB , D2 Request DB , D3 MATCH DB
                         Figure 2.3. Context Diagram of the Proposed System
The context diagram treats Dugo+ as a single system boundary that handles all internal functions,
including account management, request handling, donor matching, and notifications. Three external
entities interact with the system, Donor, Recipient, and Hospital Staff. Donors send profile data and
receive match alerts, while Recipients submit blood requests and receive status updates. Hospital
Staff send inventory updates and donor clearance confirmations, and in return receive matches and
notifications. All detailed processing, such as matching logic and eligibility checks, is handled
internally and further broken down in the Level 1 diagram.
    Lower-Level DFDs




            Figure 2.5. Level 1 Data Flow Diagram for Process 1.0 Manage Account, Process
         2.0 Submit Request, 3.0 Match Donor, 4.0 Manage Inventory and 5.0 Send Notification




​
Lower-Level DFDs




​    ​    ​    Figure 2.5. Level 2 Data Flow Diagram for Process 3.0 Match Donor
2.4​Entity Relationship Diagram




                 Figure 2.6. Entity Relationship Diagram of the Proposed System
2.4.1​Entity Description

    Entity          Purpose          Primary Key       Important Attributes        Related Entities
 Users        Stores all system    user_id          role, full_name, email,        Hospitals,
              accounts (donors,                     phone_number,                  Blood_Request
              recipients, staff,                    hashed_password,geohash        s,
              admins)                               lastDonationAt, blood_type,    Donor_Matches
                                                    date_of_birth, latitude,       , Donations,
                                                    longitude, eligibility_info,   Reward_Transa
                                                    is_verified, status,           ction,
                                                    hospital_id                    Inventory_Logs,
                                                                                   Notifications,
                                                                                            Data_Subject_
                                                                                            Request,
                                                                                            Donor_Consent
                                                                                            s,
                                                                                            System_Config

Hospitals         Stores partner            hospital_id      name, address, latitude,       Users,
                  hospital details and                       longitude, contact_number,     Subscriptions,
                  locations                                  status, created_by             Blood_Request
                                                                                            s,
                                                                                            Blood_Inventor
                                                                                            y

Subscriptions     Tracks a hospital's       subscription_i   hospital_id, plan,             Hospitals
                  subscription plan         d                start_date, end_date, status
                  and validity

Blood_Reque       Records emergency         request_id       recipient_id, hospital_id,     Hospitals,
sts               or regular blood                           created_by, blood_type,        Users,
                  requests posted by                         quantity, urgency_level,       Donor_Matches
                  or for hospitals​                          status, created_at             , Notifications

Donor_Match       Links a donor to a        match_id         request_id, donor_id,          Blood_Request
es                blood request and                          donation_type_id,              s, Users,
                  tracks their response                      screened_by_user_id,           Donation_Type
                  and screening                              response_status,               s, Donations,
                                                             screening_status,              Donor_Consent
                                                             guidelines_acknowledged,       s
                                                             acknowledged_at,
                                                             matched_at

Donation_Typ      Defines kinds of          donation_type    name, interval_days            Donor_Matches
es                donations and their       _id                                             ,
                  waiting intervals                                                         Eligibility_Guide
                                                                                            lines

Eligibility_Gui   Holds eligibility rules   guideline_id     donation_type_id, title,       Donation_Type
delines           shown to donors per                        description                    s
                  donation type

Donor_Conse       Records consents          consent_id       donor_id, match_id,            Users,
nts               granted or revoked                         consent_type, granted_at,      Donor_Matches
                  by donors (data                            revoked_at
                  privacy)

Donations         ​       Records           donation_id      match_id, confirmed_by,        Donor_Matches
                  completed and                              donation_date, units,          , Users,
                  confirmed donations                        confirmed_at                   Reward_Transa
                                                                                            ction,
                                                                                            Inventory_Logs

Reward_Tran       Tracks points             reward_id        donor_id, donation_id,         Users,
saction           awarded to donors                          points, awarded_at             Donations
                  for donations

Blood_Invento     Tracks blood stock        inventory_id     hospital_id (UK),              Hospitals,
ry                per blood type for                         blood_type (UK),               Inventory_Logs
                  each hospital                              units_available,
                                                             last_updated

Inventory_Log     Keeps a history of        log_id           inventory_id, donation_id,     Blood_Inventor
s                 every stock change                         user_id, change_type,          y, Donations,
                                                                  units_changed, created_at           Users

Notifications      Logs alerts sent to         notification_id    user_id, request_id,                Users,
                   users about blood                              channel, delivery_status,           Blood_Request
                   requests                                       retry_count, sent_at                s

Data_Subject       Tracks user data            dsr_id             user_id, processed_by,            Users
_Request           privacy requests                               request_type, status,
                   (access, deletion,                             created_at, resolved_at
                   etc.)

System_Conf        Holds global                config_id          updated_by,                       Users,
ig                 settings such as                               notif_retry_limit,                Radius_Tiler
                   notification retry                             notif_retry_interval,
                   rules                                          updated_at

Radius_Tiler       Defines search              tier_id            config_id, tier_order,            System_Config
                   radius tiers and wait                          radius_km, wait_minutes
                   times for donor
                   matching

Audit_Block        Tamper-evident,             block_id           prev_hash, record_hash            None
                   hash-chained audit                             (UK), event_type,                 (standalone)
                   trail of system                                hashed_entity_ref,
                   events                                         hashed_actor_ref,
                                                                  created_at




2.4.2​Data Dictionary

 Table or Entity         Field           Data Type and           Key        Null          Description or Validation
                                              Size
  Users               user_id            INT                     PK         No     Auto-generated unique user
                                                                                   ID

  Users              hospital_id         INT                     FK        Yes       References Hospitals. Set
                                                                                     only for Staff/Admin tied to
                                                                                     a hospital

  Users              role                ENUM('Donor','                    No        Account role, must be one
                                         Recipient','Staff'                          of the listed values
                                         ,'Admin')

  Users              full_name           VARCHAR(100)                      No        User's full name, letters and
                                                                                     spaces only

  Users              email               VARCHAR(255)            UK        No        Must be a valid email format
                                                                                     and unique

  Users              phone_num           VARCHAR(20)                       No        Valid PH mobile number
                     ber                                                             format (e.g.,
                                                                                     09XXXXXXXXX or
                                                                                     +639XXXXXXXXX)

  Users              hashed_pas          VARCHAR(255)                      No        Securely hashed password,
               sword                                            never stored as plain text

Users          geohash

Users          lastDonatio
               nAt

Users          blood_type        ENUM('A+','A-','         Yes   Required for donors and
                                 B+','B-','AB+','A              recipients
                                 B-','O+','O-')

Users          date_of_birt      DATE                     No    Must not be a future date.
               h                                                Donors must meet the
                                                                minimum donation age

Users          latitude          DECIMAL(9,6)             No    Range -90 to 90

Users          longitude         DECIMAL(9,6)             No    Range -180 to 180

Users          eligibility_inf   TEXT                     Yes   Donor's self-declared
               o                                                eligibility from date of birth
                                                                and last donation info

Users          is_verified       BOOLEAN                  No    Default FALSE. Set TRUE
                                                                after email verification

Users          status            ENUM('Active','          No    Default 'Active'
                                 Suspended','Re
                                 moved')

Users          created_at        TIMESTAMP                No    Default current timestamp

Hospitals      hospital_id       INT                 PK   No    Auto-generated unique
                                                                hospital ID

Hospitals      created_by        INT                 FK   No    References Users (the
                                                                admin who registered the
                                                                hospital)

Hospitals      name              VARCHAR(150)             No    Hospital name

Hospitals      address           VARCHAR(255)             No    Complete street address

Hospitals      latitude          DECIMAL(9,6)             No    Range -90 to 90

Hospitals      longitude         DECIMAL(9,6)             No    Range -180 to 180

Hospitals      contact_nu        VARCHAR(20)              No    Valid landline or mobile
               mber                                             number format

Hospitals      status            ENUM('Active','          No    Default 'Active'
                                 Suspended','Re
                                 moved')

Subscription   subscription      INT                 PK   No    Auto-generated unique
s              _id                                              subscription ID

Subscription   hospital_id       INT                 FK   No    References Hospitals
s
Subscription   plan           VARCHAR(50)              No    Subscription plan name
s

Subscription   start_date     DATE                     No    Start of the subscription
s

Subscription   end_date       DATE                     No    Must be later than
s                                                            start_date

Subscription   status         ENUM('Active','          No    Default 'Active'
s                             Suspended','Re
                              moved')

Blood_Requ     request_id     INT                 PK   No    Auto-generated unique
ests                                                         request ID

Blood_Requ     recipient_id   INT                 FK   Yes   References Users (the
ests                                                         recipient, if registered)

Blood_Requ     hospital_id    INT                 FK   No    References Hospitals
ests

Blood_Requ     created_by     INT                 FK   Yes   References Users (staff who
ests                                                         created the request)

Blood_Requ     blood_type     ENUM('A+','A-','         No    Blood type needed
ests                          B+','B-','AB+','A
                              B-','O+','O-')

Blood_Requ     quantity       INT                      No    Units needed, must be
ests                                                         greater than 0

Blood_Requ     urgency_lev    VARCHAR(20)              No    Urgency label (e.g., Low,
ests           el                                            Medium, High, Critical)

Blood_Requ     status         ENUM('Active',​          No    Default 'Active'
ests                          'Matched',​
                              'Completed’,​
                              ‘Cancelled,
                              ‘Expired')

Blood_Requ     created_at     TIMESTAMP                No    Default current timestamp
ests

Donor_Matc     match_id       INT                 PK   No    Auto-generated unique
hes                                                          match ID

Donor_Matc     request_id     INT                 FK   No    References
hes                                                          Blood_Requests

Donor_Matc     donor_id       INT                 FK   No    References Users (role
hes                                                          must be Donor)

Donor_Matc     donation_ty    INT                 FK   No    References Donation_Types
hes            pe_id

Donor_Matc     screened_b     INT                 FK   Yes   References Users (staff who
hes            y_user_id                                     screened the donor)

Donor_Matc     response_st    VARCHAR(20)              No    Donor's response (e.g.,
hes              atus                                          Pending, Accepted,
                                                               Declined)

Donor_Matc       screening_s    ENUM('Cleared'           Yes   Set after screening by staff
hes              tatus          ,'Deferred','Reje
                                cted')

Donor_Matc       guidelines_    BOOLEAN                  No    Default FALSE. Must be
hes              acknowledg                                    TRUE before screening
                 ed

Donor_Matc       acknowledg     TIMESTAMP                Yes   Required when
hes              ed_at                                         guidelines_acknowledged is
                                                               TRUE

Donor_Matc       matched_at     TIMESTAMP                No    Default current timestamp
hes

Donation_Ty      donation_ty    INT                 PK   No    Auto-generated unique type
pes              pe_id                                         ID

Donation_Ty      name           VARCHAR(50)              No    Type name (e.g., Whole
pes                                                            Blood, Platelets)

Donation_Ty      interval_day   INT                      No    Minimum days between
pes              s                                             donations, must be greater
                                                               than 0

Eligibility_Gu   guideline_id   INT                 PK   No    Auto-generated unique
idelines                                                       guideline ID

Eligibility_Gu   donation_ty    INT                 FK   No    References Donation_Types
idelines         pe_id

Eligibility_Gu   title          VARCHAR(100)             No    Short guideline title
idelines

Eligibility_Gu   description    TEXT                     No    Full guideline text shown to
idelines                                                       donors

Donor_Cons       consent_id     INT                 PK   No    Auto-generated unique
ents                                                           consent ID

Donor_Cons       donor_id       INT                 FK   No    References Users
ents

Donor_Cons       match_id       INT                 FK   Yes   References
ents                                                           Donor_Matches. Null for
                                                               general consents

Donor_Cons       consent_typ    VARCHAR(50)              No    Type of consent given (e.g.,
ents             e                                             Data Sharing, Screening)

Donor_Cons       granted_at     TIMESTAMP                No    When consent was granted
ents

Donor_Cons       revoked_at     TIMESTAMP                Yes   Null while consent is active.
ents                                                           Must be after granted_at

Donations        donation_id    INT                 PK   No    Auto-generated unique
                                                              donation ID

Donations      match_id       INT                 FK,   No    References
                                                  UK          Donor_Matches. One
                                                              donation per match

Donations      confirmed_     INT                 FK    No    References Users (staff who
               by                                             confirmed)

Donations      donation_d     DATE                      No    Must not be a future date
               ate

Donations      units          INT                       No    Units donated, must be
                                                              greater than 0

Donations      confirmed_     TIMESTAMP                 No    When staff confirmed the
               at                                             donation

Reward_Tra     reward_id      INT                 PK    No    Auto-generated unique
nsaction                                                      reward ID

Reward_Tra     donor_id       INT                 FK    No    References Users
nsaction

Reward_Tra     donation_id    INT                 FK,   No    References Donations. One
nsaction                                          UK          reward per donation

Reward_Tra     points         INT                       No    Points awarded, must be
nsaction                                                      greater than 0

Reward_Tra     awarded_at     TIMESTAMP                 No    Default current timestamp
nsaction

Blood_Invent   inventory_id   INT                 PK    No    Auto-generated unique
ory                                                           inventory ID

Blood_Invent   hospital_id    INT                 FK,   No    References Hospitals
ory                                               UK*

Blood_Invent   blood_type     ENUM('A+','A-','    UK*   No    *Unique together with
ory                           B+','B-','AB+','A               hospital_id
                              B-','O+','O-')

Blood_Invent   units_availa   INT                       No    Current stock, cannot be
ory            ble                                            negative

Blood_Invent   last_update    TIMESTAMP                 No    Auto-updated on every
ory            d                                              stock change

Inventory_Lo   log_id         INT                 PK    No    Auto-generated unique log
gs                                                            ID

Inventory_Lo   inventory_id   INT                 FK    No    References Blood_Inventory
gs

Inventory_Lo   donation_id    INT                 FK    Yes   References Donations. Set
gs                                                            only for donation-based
                                                              additions

Inventory_Lo   user_id        INT                 FK    No    References Users (who
gs                                                       made the change)

Inventory_Lo    change_typ      VARCHAR(30)        No    Type of change (e.g.,
gs              e                                        Donation, Usage,
                                                         Adjustment, Expired)

Inventory_Lo    units_chang     INT                No    Positive for additions,
gs              ed                                       negative for deductions

Inventory_Lo    created_at      TIMESTAMP          No    Default current timestamp
gs

Notifications   notification_   INT           PK   No    Auto-generated unique
                id                                       notification ID

Notifications   user_id         INT           FK   No    References Users (recipient
                                                         of the alert)

Notifications   request_id      INT           FK   No    References
                                                         Blood_Requests

Notifications   channel         VARCHAR(20)        No    Delivery channel (e.g.,
                                                         Push, Email)

Notifications   delivery_sta    VARCHAR(20)        No    Status (e.g., Pending, Sent,
                tus                                      Failed)

Notifications   retry_count     INT                No    Default 0. Must not exceed
                                                         notif_retry_limit

Notifications   sent_at         TIMESTAMP          Yes   Null until successfully sent

Data_Subjec     dsr_id          INT           PK   No    Auto-generated unique
t_Request                                                request ID

Data_Subjec     user_id         INT           FK   No    References Users (the data
t_Request                                                subject)

Data_Subjec     processed_      INT           FK   Yes   References Users (admin
t_Request       by                                       who handled it)

Data_Subjec     request_typ     VARCHAR(30)        No    Type (e.g., Access,
t_Request       e                                        Correction, Deletion)

Data_Subjec     status          VARCHAR(20)        No    Status (e.g., Pending, In
t_Request                                                Progress, Resolved,
                                                         Rejected)

Data_Subjec     created_at      TIMESTAMP          No    Default current timestamp
t_Request

Data_Subjec     resolved_at     TIMESTAMP          Yes   Null until resolved
t_Request

System_Con      config_id       INT           PK   No    Auto-generated unique
fig                                                      config ID

System_Con      updated_by      INT           FK   No    References Users (admin
fig                                                      who last changed it)
System_Con     notif_retry_li   INT                 No    Max notification retries,
fig            mit                                        must be 0 or greater

System_Con     notif_retry_i    INT                 No    Minutes between retries,
fig            nterval                                    must be greater than 0

System_Con     updated_at       TIMESTAMP           No    Auto-updated on every
fig                                                       change

Radius_Tiler   tier_id          INT            PK   No    Auto-generated unique tier
                                                          ID

Radius_Tiler   config_id        INT            FK   No    References System_Config

Radius_Tiler   tier_order       INT                 No    Search order (1 is searched
                                                          first)

Radius_Tiler   radius_km        DECIMAL(5,2)        No    Search radius in kilometers,
                                                          must be greater than 0

Radius_Tiler   wait_minute      INT                 No    Minutes to wait before
               s                                          expanding to the next tier

Audit_Block    block_id         BIGINT         PK   No    Auto-generated unique
                                                          block ID

Audit_Block    prev_hash        CHAR(64)            Yes   Hash of the previous block.
                                                          Null for the first block

Audit_Block    record_has       CHAR(64)       UK   No    SHA-256 hash of this
               h                                          record, must be unique

Audit_Block    event_type       VARCHAR(50)         No    Type of event logged

Audit_Block    hashed_enti      CHAR(64)            No    Hashed reference to the
               ty_ref                                     affected entity

Audit_Block    hashed_act       CHAR(64)            No    Hashed reference to the
               or_ref                                     user who acted

Audit_Block    created_at       TIMESTAMP           No    Default current timestamp
2.5​Use Case Diagram




               Figure 2.7. Use Case Diagram of the Proposed System
2.5.1​Use Case Summary

      Use Case     Use Case Name        Primary Actor                 Brief Description
         ID
     UC-001      Register              Donor, Recipient    Allows a new Donor or Recipient to
                                                           create a verified Dugo+ account using
                                                           personal information, consent, and
                                                           email verification.

     UC-002      Login                 Donor, Recipient,   Allows users to securely access the
                                       Hospital, System    functions and dashboard permitted for
                                       Admin               their account role.

     UC-003      Create/Edit Profile   Donor, Recipient    Allows users to create or update
                                                           personal information, including blood
                                                           type, contact information, and location.

     UC-004      View Available        Donor               Allows Donors to view active blood
                 Requests                                  requests filtered according to blood
                                                           compatibility and proximity.

     UC-005      View Health Tracker Donor                 Allows Donors to view donation
                                                           eligibility information, waiting periods,
                                                           and recommended next donation
                                                           dates.

     UC-006      Accept/Decline        Donor               Allows Donors to accept or decline an
                 Request                                   active blood request after reviewing
                                                           the applicable eligibility guidelines.

     UC-007      Submit Blood          Recipient           Allows Recipients to submit blood
                 Request                                   requests and initiate matching with
                                                           compatible and nearby Donors.

     UC-008      Track Donation        Donor               Allows Donors to view their verified
                 History                                   previous blood donation records

     UC-009      Receive Emergency Donor                   Sends emergency alerts to compatible
                 Notifications                             and eligible Donors through configured
                                                           email channels.

     UC-010      View                  Donor               Allows Donors to view their earned
                 Points/Rewards                            reward points and available rewards
                                                           from completed donations.

     UC-011      View Total Units      Hospital            Allows Hospital staff to view the total
                 Collected                                 number of blood units collected over a
                                                           selected period.
     UC-012      Create Blood          Hospital            Allows Hospital staff to create blood
                 Requests                                  requests on behalf of patients and
                                                           initiate Donor matching.
     UC-013      View Active           Hospital            Allows Hospital staff to monitor active
                 Requests                                  blood requests and their current
                                                           status.
     UC-014      View Blood            Hospital            Allows authorized Hospital staff to
         Donation History                         review a Donor’s recorded donation
                                                  history
UC-015   Manage               Hospital            Allows Hospital staff to view and
         Subscription Plan                        manage the hospital’s Dugo+
                                                  subscription plan.

UC-016   Secure Donor         Hospital            Allows Hospital staff to access Donor
         Information                              information only when authorized and
                                                  applicable consent is recorded.

UC-017   Check Blood          Hospital            Allows Hospital staff to view current
         Inventory                                blood inventory by blood type,
                                                  quantity, and other recorded details.

UC-018   Edit Hospital Profile Hospital           Allows authorized Hospital staff to
                                                  update hospital information such as
                                                  facility details, contact information, and
                                                  location.

UC-019   View Nearby          Donor               Allows Donors to locate nearby
         Hospital on Map                          hospitals using the system map and
                                                  available location information.

UC-020   Submit Emergency     Hospital            Allows Hospital staff to submit urgent
         Blood Donation                           blood requests, initiate matching, and
         Requests                                 trigger emergency notifications.

UC-021   Logout               Donor, Recipient,   Allows authenticated users to securely
                              Hospital, System    end their current Dugo+ session.
                              Admin

UC-022   View Matched         Donor, Recipient    Allows a Donor or Recipient to view
         Party’s Location                         the permitted location of the matched
                                                  party after a successful match

UC-023   View and               Donor             Allows Donors to review applicable
         Acknowledge                              donation guidelines and record
         Eligibility Guidelines                   acknowledgment before accepting a
                                                  request.
UC-024   Reset Password /     Donor, Recipient,   Allows users to recover account
         Account Recovery     Hospital            access by verifying their identity and
                                                  resetting their password.

UC-025   Request Data         Donor, Recipient    Allows users to submit requests to
         Access/Correction/                       access, correct, or delete their
         Deletion                                 personal data held by Dugo+.

UC-026   Update Blood         Hospital            Allows Hospital staff to add or update
         Inventory                                inventory records following donations
                                                  or transfusions and record the related
                                                  audit event.
UC-027   Verify Donor         Hospital            Allows Hospital staff to record the final
         Eligibility                              Donor screening result as Cleared,
                                                  Deferred, or Rejected.

UC-028   Configure System     System Admin        Allows the System Admin to configure
         Parameters                               system-wide matching radius and
                                                  notification retry parameters.
       UC-029          Manage User             System Admin            Allows the System Admin to create
                       Accounts                                        Hospital accounts and suspend or
                                                                       remove authorized user accounts

       UC-030          Process Data            System Admin            Allows the System Admin to review
                       Subject Request                                 and process requests for personal
                                                                       data access,

       UC-031          View Audit Log          Hospital, System        Allows authorized users to review
                                               Admin                   blockchain-based audit records for
                                                                       donation, inventory, and data-access
                                                                       events.
       UC-032          Verify Audit Record     System Admin            Allows the System Admin to verify
                       Integrity                                       whether an audit record has been
                                                                       altered by checking its stored hash
                                                                       against the blockchain.

       UC-033          View Profile            System Admin            Allows the System Admin to view their
                                                                       own administrator profile information.


       UC-034          View Hospital           Hospital                Allows Hospital staff to view the
                       Location on Map                                 hospital’s saved location on the
                                                                       system map.




2.5.2​Detailed Use Case Description

            Field                                                     Description

Use Case ID and Name          UC-001 — Register


Primary Actor                 Donor, Recipient


Goal                          Create an account to access Dugo+.


Trigger                       The user selects Register from the login page.


Preconditions                 The user has a mobile device, an internet connection, and a reachable contact number.


Main Flow                     1. The user opens the registration form.​
                              2. The user enters the required personal details, blood type, contact information,
                              username, and password. The user then selects a role: Donor or Recipient.​
                              3. The system presents a consent form for the user to read and agree to before their
                              information is shared with the hospital.​
                              4. The system validates the submitted information.​
                              5. The system sends an email containing a verification link to the user's registered email
                              address.​
                              6. The user opens the email and clicks the verification link.​
                              7. The system verifies the user's email address and creates the account with the
                              selected role (Donor or Recipient).​
                              8. The system confirms successful registration and directs the user to the login page.

                              3a. A required field is missing or a value is invalid: The system identifies the field and
Alternative or Exception      asks the user to correct it.​
Flow                          3b. The username is already in use: The system displays an error and requests a
                           different username.

                           3c. The password does not meet the minimum length or complexity requirement: The
                           system displays the password requirements.​
                           4a. Email delivery fails: The system informs the user and offers to resend the verification
                           email when available.​
                           5a. The email verification link is invalid or expired: The system rejects the link and asks
                           the user to request a new verification email.



Postconditions             Success: A verified Donor or Recipient account is created and is available for login.
                           Failure: No account is created; entered information remains unregistered.




            Field                                                 Description

Use Case ID and Name       UC-002 — Login


Primary Actor              Donor, Recipient, Hospital, System Admin


Goal                       Access the functions permitted for the user's account role.


Trigger                    The user opens Dugo+ and the login page is displayed.


Preconditions              The user has an existing account and valid login credentials. Hospital and System
                           Admin users use their assigned role-based credentials.


Main Flow                  1. The user opens the login page.​
                           2. The user enters the registered username and password or the assigned credentials.​
                           3. The system validates the credentials and account status.​
                           4. The system establishes an authenticated session.​
                           5. The system displays the dashboard appropriate to the user's role.


Alternative or Exception   2a. A required field is empty: The system prompts the user to complete it.​
Flow                       3a. The credentials are incorrect or the account cannot be used: The system displays
                           an error without opening a session.​
                           3b. The account is suspended or removed: The system denies access and displays an
                           appropriate message.​
                           3c. The internet connection is unavailable: The system reports the connection problem
                           and does not establish a session.


Postconditions             Success: An authenticated session is active and the role-appropriate dashboard is
                           displayed. Failure: No authenticated session is created.


            Field                                                 Description

Use Case ID and Name       UC-003 — Create/Edit Profile


Primary Actor              Donor, Recipient


Goal                       Create or update personal profile information used by Dugo+.


Trigger                    The user opens the profile page after logging in.
Preconditions              The user is logged in.


Main Flow                  1. The user opens the profile page.​
                           2. The system displays the existing profile, if one exists.​
                           3. The user enters or edits the applicable personal details, including name, blood type,
                           date of birth, contact information, location, and eligibility information.​
                           4. The system validates the entered information.​
                           5. The system saves the valid profile information.​
                           6. The system displays the updated profile and a confirmation message.


Alternative or Exception   3a. The user cancels the operation: The system discards unsaved changes.​
Flow                       3b. Location permission is unavailable: The system allows the user to provide a location
                           manually, where supported.​
                           4a. A required field is missing or a value is invalid: The system identifies the issue and
                           requests correction.​
                           5a. The information cannot be saved: The system displays an error and retains the
                           previously saved profile.


Postconditions             Success: The user's profile is created or updated. Failure or cancellation: The
                           previously saved profile remains unchanged.


            Field                                                 Description

Use Case ID and Name       UC-004 — View Available Requests


Primary Actor              Do

                           nor


Goal                       Browse active blood requests that may match the donor's blood type and proximity.


Trigger                    The Donor opens the Available Requests section.


Preconditions              The Donor is logged in and has a profile containing blood type and location information.


Main Flow                  1. The Donor opens the Available Requests section.​
                           2. The system retrieves active blood requests.​
                           3. The system filters or presents requests according to blood type compatibility and the
                           configured proximity search.​
                           4. The system displays available request details, including blood type, urgency, hospital,
                           and distance when available.​
                           5. The Donor selects a request to view its details.


Alternative or Exception   2a. No active or matching requests are found: The system displays a message that no
Flow                       available requests were found.​
                           2b. Request information cannot be retrieved: The system displays an error and provides
                           a retry option.​
                           3a. Location information is unavailable: The system indicates that proximity-based
                           results may be limited or asks the Donor to provide location access.


Postconditions             Success: The available request list or selected request details are displayed. If no
                           results exist, the system displays an empty-state message without changing any
                           request.


            Field                                                 Description
Use Case ID and Name       UC-005 — View Health Tracker


Primary Actor              Donor


Goal                       View donation eligibility information and the recommended next donation date.


Trigger                    The Donor selects Health Tracker.


Preconditions              The Donor is logged in.


Main Flow                  1. The Donor opens Health Tracker.​
                           2. The system retrieves the Donor's verified donation history and applicable profile
                           information.​
                           3. The system determines the applicable waiting period based on the donation type and
                           latest verified donation record.​
                           4. The system displays the eligibility status, relevant waiting-period information, and
                           recommended next donation date, where determinable.


Alternative or Exception   2a. No verified donation record exists: The system displays the available default or
Flow                       undetermined status.​
                           2b. The required information cannot be retrieved: The system displays an error and
                           allows the Donor to retry.​
                           3a. The waiting period has not elapsed: The system displays that the Donor is not yet
                           eligible and shows the applicable remaining period.


Postconditions             Success: The current eligibility information available to the system is displayed. The
                           tracker does not itself constitute final medical clearance for donation.


            Field                                                 Description

Use Case ID and Name       UC-006 — Accept/Decline Request


Primary Actor              Donor


Goal                       Respond to an active blood request by accepting or declining it.


Trigger                    The Donor selects an active request from the request list or opens it from a notification.


Preconditions              The Donor is logged in and the request is active. To accept, the Donor must satisfy the
                           system's recorded eligibility rules and acknowledge the displayed guidelines.


Main Flow                  1. The Donor opens the request details.​
                           2. The system displays the request information and applicable eligibility guidelines.​
                           3. The Donor chooses Accept or Decline.​
                           4. If Accept is selected, the Donor confirms that they have read and acknowledged the
                           displayed guidelines.|​
                           6.The system shall send a consent form for the users to read before validating and
                           sharing their information before being accessed by the hospital. ​
                           6. The system validates the response and rechecks that the request is still active.​
                           7. The system records the Donor's response and acknowledgment and shows the name
                           of the Recipient and hospital, including its date and time when accepted and routes both
                           parties to the hospital for final eligibility verification .​
                           8. The system updates the request response status and informs the relevant parties
                           according to the request workflow.
Alternative or Exception   3a. The Donor selects Decline: The system records the decline and leaves the request
Flow                       available to other potential donors, if it remains active.​
                           4a. The Donor does not acknowledge the guidelines: The system prevents acceptance
                           and asks the Donor to acknowledge them.​
                           5a. The Donor does not meet a system-recorded waiting-period rule: The system blocks
                           acceptance and displays the eligibility information.​
                           5b. The request has been fulfilled, cancelled, or expired: The system does not record an
                           acceptance and informs the Donor.​
                           4b. The Donor cancels before confirmation: The system makes no change to the
                           response.


Postconditions             Success: The response is recorded; an accepted response includes the required
                           acknowledgment record. Decline: The decline is recorded and the request may remain
                           open. Failed or cancelled acceptance: No acceptance is recorded.




            Field                                                Description

Use Case ID and Name       UC-007 — Submit Blood Request


Primary Actor              Recipient


Goal                       Submit a blood request so the system can search for compatible donors.


Trigger                    The Recipient selects the blood request function.


Preconditions              The Recipient is logged in and has the information needed to complete the request.


Main Flow                  1. The Recipient opens the blood request form.​
                           2. The Recipient enters the required blood type, quantity, urgency, hospital location, and
                           other requested details.​
                           3. The system validates the request information.​
                           4. The Recipient submits the request.​
                           5. The system saves the request and initiates donor matching using the configured
                           compatibility and proximity rules.​
                           6. The system displays a submission confirmation and the current request status.


Alternative or Exception   2a. Required information is missing or invalid: The system identifies the issue and asks
Flow                       the Recipient to correct it.​
                           3a. The quantity or another value is outside the accepted format: The system displays a
                           validation message.​
                           4a. The internet connection is unavailable: The system reports that the request was not
                           submitted.​
                           5a. No compatible eligible donors are found: The system keeps the request active,
                           where applicable, and informs the Recipient that no match is currently available.


Postconditions             Success: The request is saved and matching is initiated. If no donor is found, the
                           request remains active where applicable. Failed submission: No new request is created.


            Field                                                Description

Use Case ID and Name       UC-008 — Track Donation History


Primary Actor              Donor
Goal                       Review the Donor's recorded donation history.


Trigger                    The Donor opens the Donation History section.


Preconditions              The Donor is logged in.


Main Flow                  1. The Donor opens Donation History.​
                           2. The system retrieves the Donor's verified donation records.​
                           3. The system displays the records, including available dates, locations, hospitals or
                           blood banks, and donation status.​
                           4. The Donor selects a record to view its details, if available.


Alternative or Exception   2a. No completed donation records exist: The system displays a message indicating
Flow                       that no donation history is available.​
                           2b. The records cannot be retrieved: The system displays an error and allows the Donor
                           to retry.


Postconditions             Success: The Donor's available donation history is displayed. No donation records are
                           changed.


            Field                                                 Description

Use Case ID and Name       UC-009 — Receive Emergency Notifications


Primary Actor              Donor


Goal                       Receive an alert when a compatible and eligible match is found for an emergency blood
                           request.


Trigger                    The system identifies the Donor as a compatible and eligible match for an emergency
                           request.


Preconditions              The Donor has an account with usable contact information. The request is active, and
                           the Donor satisfies the configured matching criteria.


Main Flow                  1. The system detects or receives an emergency blood request.​
                           2. The matching process identifies nearby Donors who meet the applicable compatibility
                           and eligibility criteria.​
                           3. The system sends an emergency notification to matched Donors through the
                           configured email channels.​
                           4. The Donor opens the notification or the Dugo+ application.​
                           5. The system displays the related request details and current status.


Alternative or Exception   2a. No compatible and eligible Donor is found: The system sends no match notification
Flow                       and the request remains subject to its active-request workflow.​
                           3a. email delivery fails: The system retains the request as active and retries notification
                           delivery according to its retry settings.​
                           4a. The request is no longer active: The system displays the current status rather than
                           treating the request as available.


Postconditions             Success: A notification is attempted for each identified match and the request remains
                           traceable. Notification failure does not by itself cancel the request.


            Field                                                 Description
Use Case ID and Name       UC-010 — View Points/Rewards


Primary Actor              Donor


Goal                       View reward points earned from completed donations.


Trigger                    The Donor selects the Points or Rewards section.


Preconditions              The Donor is logged in.


Main Flow                  1. The Donor opens the Points or Rewards section.​
                           2. The system retrieves the Donor's points balance and recorded reward information.​
                           3. The system displays the current points balance and available reward information.​
                           4. The Donor selects a reward, if available, to view its details.


Alternative or Exception   2a. The Donor has no points: The system displays a zero balance.​
Flow                       2b. Reward information cannot be retrieved: The system displays an error and allows
                           the Donor to retry.​
                           4a. A selected reward is unavailable or its requirements are not met: The system
                           displays the applicable status or requirements.


Postconditions             Success: The current points balance and available reward information are displayed.
                           Viewing rewards does not alter the points balance.


            Field                                                  Description

Use Case ID and Name       UC-011 — View Total Units Collected


Primary Actor              Hospital


Goal                       View the total number of blood units collected over a selected period.


Trigger                    Hospital staff select View Total Units Collected on the dashboard.


Preconditions              Hospital staff are logged in and collection records are available, if any.


Main Flow                  1. Hospital staff open the hospital dashboard.​
                           2. Hospital staff select View Total Units Collected and specify a period, if the feature
                           requests one.​
                           3. The system retrieves the relevant completed-donation or collection records.​
                           4. The system calculates the total units recorded for the selected period.​
                           5. The system displays the total, grouped by blood type where supported.


Alternative or Exception   2a. The selected period is invalid: The system asks Hospital staff to correct the period.​
Flow                       3a. No units have been recorded for the period: The system displays a zero total or an
                           appropriate no-records message.​
                           3b. The records cannot be retrieved: The system displays an error and allows Hospital
                           staff to retry.


Postconditions             Success: The total units collected for the selected period are displayed. No collection
                           records are modified.


            Field                                                  Description
Use Case ID and Name       UC-012 — Create Blood Requests


Primary Actor              Hospital


Goal                       Create a blood request on behalf of a patient and initiate donor matching.


Trigger                    Hospital staff select Create Blood Request.


Preconditions              Hospital staff are logged in and have the required patient blood-request information.


Main Flow                  1. Hospital staff select Create Blood Request.​
                           2. The system displays the request form.​
                           3. Hospital staff enter the required blood type, quantity, urgency, hospital location, and
                           other required request details.​
                           4. Hospital staff submit the form.​
                           5. The system validates the entered information.​
                           6. The system saves the request as active and initiates matching against compatible,
                           eligible nearby Donors.​
                           7. The system displays the request status and sends the configured notifications to
                           matched Donors.


Alternative or Exception   3a. Required information is missing or invalid: The system identifies the fields that need
Flow                       correction.​
                           5a. Validation fails: The system does not save the request and displays an error.​
                           6a. No compatible and eligible Donors are found: The system informs Hospital staff and
                           retains the request as active where applicable.​
                           7a. A notification service is unavailable: The system reports the delivery issue and
                           follows its retry process.


Postconditions             Success: The hospital request is saved and matching is initiated. Failure: The request is
                           not saved if validation fails.


            Field                                                 Description

Use Case ID and Name       UC-013 — View Active Requests


Primary Actor              Hospital


Goal                       Review active blood requests and monitor their current status.


Trigger                    Hospital staff select Active Requests on the dashboard.


Preconditions              Hospital staff are logged in.


Main Flow                  1. Hospital staff open Active Requests.​
                           2. The system retrieves active requests and prioritizes them by urgency associated with
                           the hospital or facility.​
                           3. The system displays the requests with available details such as blood type, urgency,
                           submission information, and current status.​
                           4. Hospital staff select a request to view its details.


Alternative or Exception   2a. No active requests exist: The system displays a no-active-requests message.​
Flow                       2b. The system cannot retrieve request information: The system displays an error and
                           allows Hospital staff to retry.
Postconditions             Success: The active request list or selected request details are displayed. No request
                           status is changed by viewing.


            Field                                                  Description

Use Case ID and Name       UC-014 — View Blood Donation History


Primary Actor              Hospital


Goal                       Review a Donor's recorded donation history for operational and eligibility reference.


Trigger                    Hospital staff select a Donor record and request its donation history.


Preconditions              Hospital staff are logged in, the Donor has a registered profile, and the required access
                           authorization and consent are present.


Main Flow                  1. Hospital staff locate and select a Donor record.​
                           2. Hospital staff select View Blood Donation History.​
                           3. The system checks the staff member's access rights and the applicable consent.​
                           4. The system retrieves the Donor's recorded donation history.​
                           5. The system displays the donation records available to the authorized staff member.


Alternative or Exception   3a. The staff member is not authorized or the required consent is absent: The system
Flow                       denies access and does not display the protected history.​
                           4a. No donation records exist: The system displays a no-history message.​
                           4b. The history cannot be retrieved: The system displays an error and allows an
                           authorized user to retry.


Postconditions             Success: Authorized Hospital staff can view the available history. Denied or failed
                           access does not expose the protected records.


            Field                                                  Description

Use Case ID and Name       UC-015 — Manage Subscription Plan


Primary Actor              Hospital


Goal                       View and manage the hospital's subscription plan for Dugo+ access.


Trigger                    Hospital staff open Subscription Plan from the hospital dashboard.


Preconditions              Hospital staff are logged in with permission to manage the hospital subscription.


Main Flow                  1. Hospital staff open Subscription Plan.​
                           2. The system displays the hospital's current subscription information.​
                           3. Hospital staff select an available plan or choose to retain the current plan.​
                           4. If a change is selected, the system validates the requested plan change.​
                           5. The system saves the plan change when valid.​
                           6. The system displays the resulting subscription status.


Alternative or Exception   3a. Hospital staff cancel the change: The system retains the current plan.​
Flow                       4a. The requested plan is invalid or unavailable: The system displays an error and does
                           not apply the change.​
                           5a. The change cannot be saved: The system reports the error and retains the previous
                           plan.


Postconditions             Success: The selected valid plan is recorded, or the current plan is retained. This use
                           case does not assume an online payment function.


            Field                                                Description

Use Case ID and Name       UC-016 — Secure Donor Information


Primary Actor              Hospital


Goal                       Access donor information only when authorized and when applicable consent is
                           recorded.


Trigger                    Hospital staff request access to a Donor's protected information.


Preconditions              Hospital staff are logged in; the Donor information exists; and applicable access
                           authorization and consent requirements can be checked.


Main Flow                  1. Hospital staff request a Donor's information.​
                           2. The system verifies the staff member's identity and role-based access rights.​
                           3. The system checks whether the required Donor consent is recorded.​
                           4. The system retrieves only the information the staff member is authorized to access.​
                           5. The system displays the permitted information and records the access event in the
                           audit trail.


Alternative or Exception   2a. The staff member is not authorized: The system denies access.​
Flow                       3a. Required consent is not recorded: The system does not disclose the Donor's
                           protected information.​
                           4a. The information cannot be retrieved: The system displays an error without exposing
                           unauthorized data.


Postconditions             Success: Only authorized and consent-permitted information is displayed, and the
                           access event is auditable. Failure: Protected information is not disclosed.


            Field                                                Description

Use Case ID and Name       UC-017 — Check Blood Inventory


Primary Actor              Hospital


Goal                       View current blood inventory by blood type and other recorded stock details.


Trigger                    Hospital staff select Blood Inventory on the dashboard.


Preconditions              Hospital staff are logged in.


Main Flow                  1. Hospital staff open Blood Inventory.​
                           2. The system retrieves the facility's recorded inventory.​
                           3. The system displays the available stock by blood type and recorded details such as
                           quantity and expiration date.


Alternative or Exception   2a. No inventory records exist: The system displays an empty-inventory message.​
Flow                       2b. Inventory information cannot be retrieved: The system displays an error and allows
                           Hospital staff to retry.


Postconditions             Success: The current recorded inventory is displayed. Viewing inventory does not
                           change stock records.


            Field                                                   Description

Use Case ID and Name       UC-018 — Edit Hospital Profile


Primary Actor              Hospital


Goal                       Update the hospital's profile information.


Trigger                    Hospital staff select Edit Hospital Profile.


Preconditions              Hospital staff are logged in and the hospital has an existing profile.


Main Flow                  1. Hospital staff select Edit Hospital Profile.​
                           2. The system displays the current hospital profile.​
                           3. Hospital staff edit the permitted profile details, such as facility name, contact
                           information, and location.​
                           4. Hospital staff submit the changes.​
                           5. The system validates and saves the updated information.​
                           6. The system displays the updated profile and a confirmation message.


Alternative or Exception   3a. Hospital staff cancel the edit: The system discards unsaved changes.​
Flow                       5a. Required information is missing or invalid: The system identifies the problem and
                           requests correction.​
                           5b. The changes cannot be saved: The system displays an error and retains the
                           previous profile.


Postconditions             Success: The hospital profile is updated. Failure or cancellation: The previously saved
                           profile remains unchanged.


            Field                                                   Description

Use Case ID and Name       UC-019 — View Nearby Hospital on Map


Primary Actor              Donor


Goal                       View nearby hospitals on a map to identify a facility associated with blood donation.


Trigger                    The Donor selects the nearby-hospital map function.


Preconditions              The Donor is logged in and hospital location data is available. Location permission may
                           be needed for proximity-based display.


Main Flow                  1. The Donor opens the nearby-hospital map.​
                           2. The system retrieves available hospital locations.​
                           3. The system uses the Donor's location, when available, to display nearby hospitals
                           within the applicable search area.​
                           4. The system displays the hospitals on a map.​
                           5. The Donor selects a hospital marker to view its available details.
Alternative or Exception   2a. No hospital locations are available: The system displays an appropriate message.​
Flow                       3a. The Donor's location is unavailable: The system indicates that nearby sorting or
                           filtering may be limited.​
                           4a. The map service is unavailable: The system displays an error and allows the Donor
                           to retry.


Postconditions             Success: Available hospital locations are displayed on the map. No hospital records are
                           modified.


            Field                                                Description

Use Case ID and Name       UC-020 — Submit Emergency Blood Donation Requests


Primary Actor              Hospital


Goal                       Submit an urgent blood request and initiate matching and emergency notifications.


Trigger                    A Recipient or Hospital staff member identifies an emergency need and selects the
                           emergency request function.


Preconditions              The actor is authenticated; the required blood type and request information are
                           available; Hospital staff use an authorized hospital account.


Main Flow                  1. The actor opens the emergency blood request form.​
                           2. The actor enters the required blood type, quantity, urgency, hospital location, and
                           other required information.​
                           3. The system validates the information and identifies the request as an emergency.​
                           4. The actor submits the request.​
                           5. The system saves the valid request as active.​
                           6. The system searches for compatible and eligible Donors using the configured tiered
                           proximity radius.​
                           7. The system sends emergency notifications to matched Donors through email and
                           displays the request status to the submitting actor.


Alternative or Exception   2a. Required information is missing or invalid: The system asks the actor to correct the
Flow                       form.​
                           3a. The request fails validation: The system does not save it and displays an error.​
                           6a. No eligible match is found within the configured search range: The system informs
                           the actor and retains the request as active where applicable.​
                           7a. email delivery fails: The system retains the active request and retries notification
                           delivery according to its settings.


Postconditions             Success: The emergency request is saved and matching is initiated. If no match is
                           found, the request remains active where applicable. Failed validation results in no new
                           request.


            Field                                                Description

Use Case ID and Name       UC-021 — Logout


Primary Actor              Donor, Recipient, Hospital, System Admin


Goal                       Securely end the current Dugo+ session.


Trigger                    The user selects Logout.
Preconditions              The user has an active authenticated session.


Main Flow                  1. The user selects Logout.​
                           2. The system invalidates the active session.​
                           3. The system returns the user to the login screen.


Alternative or Exception   2a. The session has already expired: The system returns the user to the login screen
Flow                       and does not retain an active session.​
                           2b. The logout request cannot be completed because of a connection issue: The
                           system informs the user; the session must not be treated as successfully ended until
                           invalidation is confirmed.


Postconditions             Success: The active session is ended and the login screen is displayed. If the session
                           had already expired, the user remains unauthenticated.


            Field                                                 Description

Use Case ID and Name       UC-022 — View Matched Party's Location


Primary Actor              Donor, Recipient


Goal                       View the location of the relevant matched party after a match is established.


Trigger                    The Donor or Recipient opens a matched request and selects the location option.


Preconditions              The user is logged in, a match exists, and location information is available for disclosure
                           under the system's consent and access rules.


Main Flow                  1. The user opens the matched request details.​
                           2. The user selects View Matched Party's Location.​
                           3. The system verifies that a match exists and that the user is permitted to view the
                           location.​
                           4. The system retrieves the permitted location information.​
                           5. The system displays the matched party's location.


Alternative or Exception   3a. No match exists or the user is not authorized: The system denies the location
Flow                       request.​
                           4a. Location information is unavailable: The system informs the user that the location
                           cannot be displayed.​
                           5a. The map or location service is unavailable: The system displays an error and allows
                           a retry.


Postconditions             Success: The authorized user views the available matched-party location. Failure: No
                           restricted location information is disclosed.


            Field                                                 Description

Use Case ID and Name       UC-023 — View and Acknowledge Eligibility Guidelines


Primary Actor              Donor


Goal                       Review the donation eligibility guidelines applicable to a selected donation type and
                           acknowledge having read them.
Trigger                    The Donor opens the eligibility guidelines before accepting a blood request.


Preconditions              The Donor is logged in and a donation type or applicable request has been selected.


Main Flow                  1. The Donor opens the eligibility guidelines.​
                           2. The system displays the guidelines relevant to the selected donation type, including
                           applicable waiting periods and relevant eligibility considerations.​
                           3. The Donor reviews the displayed guidelines.​
                           4. The Donor checks the acknowledgment box to confirm that the guidelines have been
                           read and that they meet the displayed criteria.​
                           5. The system records the acknowledgement and its date and time.​
                           6. The system makes the acknowledgment available to the related request workflow.


Alternative or Exception   2a. The guidelines cannot be loaded: The system displays an error and does not treat
Flow                       the guidelines as acknowledged.​
                           4a. The Donor does not check the acknowledgment box: The system does not record
                           acknowledgment and prevents acceptance where acknowledgment is required.​
                           5a. The acknowledgment cannot be saved: The system displays an error and does not
                           proceed as though it were recorded.


Postconditions             Success: The acknowledgment and its timestamp are recorded. This acknowledgment
                           does not replace the hospital's physical screening, tests, or medical-history verification.


            Field                                                 Description

Use Case ID and Name       UC-024 — Reset Password / Account Recovery


Primary Actor              Donor, Recipient, Hospital


Goal                       Recover access to an existing account by resetting its password through a verified
                           channel.


Trigger                    The user selects Forgot Password or Account Recovery from the login page.


Preconditions              The user has an existing Donor, Recipient, or Hospital account and access to its
                           registered verification channel. System Admin accounts are excluded.


Main Flow                  1. The user opens the password recovery function.​
                           2. The user provides the account identifier requested by the system.​
                           3. The system verifies that the account is eligible for recovery and initiates verification
                           through a registered channel, such as email.​
                           4. The user completes the verification step.​
                           5. The system allows the user to enter a new password.​
                           6. The system validates the new password against the password requirements.​
                           7. The system saves the new password securely and confirms that recovery is
                           complete.


Alternative or Exception   2a. The account cannot be identified: The system displays a generic recovery message.​
Flow                       3a. The verification message cannot be delivered: The system informs the user and
                           offers a retry when available.​
                           4a. Verification fails or expires: The system rejects the attempt and requests a new
                           verification step.​
                           6a. The new password does not meet requirements: The system explains the
                           requirements and requests another password.​
                           7a. The password cannot be updated: The system displays an error and does not report
                           recovery as successful.
Postconditions             Success: The account password is updated and the user can use the new password.
                           Failure: The existing password remains unchanged. System Admin recovery is outside
                           this use case.


            Field                                                 Description

Use Case ID and Name       UC-025 — Request Data Access/Correction/Deletion


Primary Actor              Donor, Recipient


Goal                       Submit a request to access, correct, or delete personal data held by Dugo+.


Trigger                    The user selects the personal data request function from their account.


Preconditions              The user is logged in and can identify the personal data request type.


Main Flow                  1. The user opens the personal data request function.​
                           2. The system displays the available request types: access, correction, or deletion.​
                           3. The user selects a request type and provides the required details.​
                           4. The system validates the request information.​
                           5. The user submits the request.​
                           6. The system records the request and provides a reference or status, where supported.


Alternative or Exception   3a. Required details are missing: The system asks the user to complete them.​
Flow                       4a. The request information is invalid: The system displays an error and requests
                           correction.​
                           5a. The request cannot be submitted because of a connection or service issue: The
                           system informs the user and does not indicate that the request was received.


Postconditions             Success: A data-subject request is recorded for review and processing. Submission
                           alone does not mean that the data has already been changed or deleted.


            Field                                                 Description

Use Case ID and Name       UC-026 — Update Blood Inventory


Primary Actor              Hospital


Goal                       Add or update blood inventory records after a completed donation or issued transfusion.


Trigger                    Hospital staff select the inventory update function following a stock-affecting event.


Preconditions              Hospital staff are logged in and authorized to update the hospital's inventory. The
                           relevant donation or transfusion information is available.


Main Flow                  1. Hospital staff open the inventory management function.​
                           2. Hospital staff select an existing inventory record or choose to add a record.​
                           3. Hospital staff enter or update the relevant information, such as blood type, quantity,
                           and expiration details, as applicable.​
                           4. The system validates the inventory information.​
                           5. Hospital staff submit the update.​
                           6. The system saves the inventory change and commits the corresponding audit record.​
                           7. The system displays the updated inventory.
Alternative or Exception   3a. Required information is missing or invalid: The system identifies the fields that need
Flow                       correction.​
                           4a. The update fails validation: The system does not apply the change.​
                           6a. The inventory update or audit-record operation fails: The system reports the failure
                           and does not display the change as successfully committed.


Postconditions             Success: The inventory record is updated and the required audit event is committed.
                           Failure: The previous inventory state remains in effect.


            Field                                                  Description

Use Case ID and Name       UC-027 — Verify Donor Eligibility


Primary Actor              Hospital


Goal                       Record the result of the hospital's final donor eligibility screening.


Trigger                    Hospital staff begin the eligibility verification for a matched Donor who reports to the
                           facility.


Preconditions              Hospital staff are logged in; a matched Donor is associated with the request; and the
                           Donor is available for screening.


Main Flow                  1. Hospital staff open the matched Donor's request or record.​
                           2. The system displays the available Donor and requests information permitted to the
                           staff member.​
                           3. Hospital staff conduct the required physical screening, blood tests, and
                           medical-history check outside or alongside the system.​
                           4. Hospital staff determine the screening result.​
                           5. Hospital staff select and submit Cleared, Deferred, or Rejected as the Donor's status​
                           6.Hospital confirms the donation is completed; system updates donation history, awards
                           points, and commits the audit record. ​
                           7. The system records the screening status and updates the associated request.​
                           8. The system makes the result available to authorized users.


Alternative or Exception   2a. The Donor or request record cannot be found: The system informs Hospital staff and
Flow                       prevents an unrelated status update.​
                           3a. Screening is incomplete: Hospital staff do not submit a final status until the
                           screening decision is available.​
                           5a. An invalid status or incomplete submission is provided: The system requests
                           correction.​
                           6a. The status update cannot be saved: The system displays an error and retains the
                           previous recorded status.


Postconditions             Success: The screening result is recorded as Cleared, Deferred, or Rejected. A
                           donation history entry is updated as completed only after Hospital staff confirm that the
                           donation was completed.


            Field                                                  Description

Use Case ID and Name       UC-028 — Configure System Parameters


Primary Actor              System Admin


Goal                       Configure system-wide matching and notification parameters.
Trigger                    System Admin opens the system parameter configuration function.


Preconditions              System Admin is logged in with permission to manage system configuration.


Main Flow                  1. System Admin opens System Parameters.​
                           2. The system retrieves and displays the current configurable values.​
                           3. System Admin edits permitted settings, including the tiered matching radius and
                           notification retry settings.​
                           4. The system validates the proposed values and their allowed ranges.​
                           5. System Admin submits the changes.​
                           6. The system saves the valid configuration.​
                           7. The system displays a confirmation and the updated settings.


Alternative or Exception   3a. System Admin cancels the changes: The system discards unsaved edits.​
Flow                       4a. A value is missing, invalid, or outside the permitted range: The system identifies the
                           setting and requests correction.​
                           6a. The configuration cannot be saved: The system displays an error and retains the
                           previous settings.


Postconditions             Success: The valid configuration is saved for system use. Failure or cancellation:
                           Existing configuration remains unchanged.


            Field                                                 Description

Use Case ID and Name       UC-029 — Manage User Accounts


Primary Actor              System Admin


Goal                       Create Hospital accounts and suspend or remove Hospital, Donor, or Recipient
                           accounts as needed.


Trigger                    System Admin opens the user account management function.


Preconditions              System Admin is logged in and authorized to manage accounts.


Main Flow                  1. System Admin opens Manage User Accounts.​
                           2. The system displays the account management options and relevant account records.​
                           3. System Admin selects an operation: create a Hospital account, suspend an account,
                           or remove an account.​
                           4. For account creation, System Admin enters the required Hospital account details. For
                           suspension or removal, System Admin selects the target account and provides the
                           required action.​
                           5. The system validates the input and checks the requested operation.​
                           6. System Admin confirms the operation.​
                           7.The system applies the authorized change and displays the resulting account status.​
                           8.The system now has its premade credentials for a hospital


Alternative or Exception   3a. Admin attempts to create a Donor/Recipient account: system refuses; those are
Flow                       self-registered only ​
                           4a. Required account information is missing or invalid: The system requests correction.​
                           5a. The target account does not exist or the operation is not permitted: The system
                           rejects the operation and displays an error.​
                           6a. System Admin cancels: The system makes no change.​
                           7a. The change cannot be saved: The system displays an error and retains the previous
                           account state.


Postconditions             Success: The authorized account is created, suspended, or removed as selected.
                           Failure or cancellation: No account change is applied.


            Field                                                 Description

Use Case ID and Name       UC-030 — Process Data Subject Request


Primary Actor              System Admin


Goal                       Review and process a user's request to access, correct, or delete personal data.


Trigger                    System Admin opens a submitted personal data request for processing.


Preconditions              System Admin is logged in and authorized to process data-subject requests. A request
                           has been submitted and recorded.


Main Flow                  1. System Admin opens the data-subject request queue.​
                           2. The system displays the submitted requests and their current status.​
                           3. System Admin selects a request and reviews its type and details.​
                           4. System Admin verifies the request and determines the appropriate action in
                           accordance with applicable requirements.​
                           5. System Admin records the processing decision and performs or coordinates the
                           approved access, correction, or deletion action.​
                           6. The system updates the request status and records the processing event.​
                           7. The system displays the updated request status.​
                           8. The system then commit an audit record when Admin accesses personal data.


Alternative or Exception   3a. The request is incomplete or requires clarification: System Admin records the need
Flow                       for additional information and leaves the request pending.​
                           4a. The request cannot be approved as submitted: System Admin records the decision
                           and applicable reason.​
                           5a. The requested action cannot be completed: The system records the issue and does
                           not mark the request as completed.​
                           6a. The status or processing event cannot be saved: The system displays an error and
                           retains the previous recorded status.


Postconditions             Success: The processing decision and resulting status are recorded. A request is
                           marked completed only when its approved action has been completed. Blockchain audit
                           records remain immutable; corrections are recorded as linked entries.


            Field                                                 Description

Use Case ID and Name       UC-031 — View Audit Log


Primary Actor              Hospital, System Admin


Goal                       Review authorized blockchain-based audit records for donation, inventory, and
                           data-access events.


Trigger                    An authorized user selects View Audit Log.


Preconditions              The user is logged in and has permission to view the audit records.


Main Flow                  1. The user opens View Audit Log.​
                           2. The system verifies the user's role and audit-log access rights.​
                           3. The system retrieves the audit records the user is authorized to view.​
                           4. The system displays the available records, including event type, timestamp, and
                           non-identifying references where applicable.​
                           5. The user selects a record to inspect its available details.


Alternative or Exception   2a. The user is not authorized: The system denies access.​
Flow                       3a. No audit records are available: The system displays an appropriate message.​
                           3b. Audit records cannot be retrieved: The system displays an error and allows an
                           authorized user to retry.


Postconditions             Success: Authorized audit records are displayed without modifying them. Unauthorized
                           users cannot view protected audit information.




            Field                                                Description

Use Case ID and Name       UC-032 — Verify Audit Record Integrity


Primary Actor              System Admin


Goal                       Check whether a blockchain audit record has been altered by verifying its hash against
                           the chain.


Trigger                    System Admin selects an audit record and requests integrity verification.


Preconditions              System Admin is logged in and authorized to verify audit records; the target audit record
                           exists.


Main Flow                  1. System Admin opens the audit log.​
                           2. System Admin selects an audit record and chooses Verify Integrity.​
                           3. The system retrieves the record's stored hash and the corresponding blockchain
                           data.​
                           4. The system performs the integrity check by comparing the record hash with the value
                           represented in the chain.​
                           5. The system displays the verification result.


Alternative or Exception   2a. The selected record cannot be found: The system informs System Admin and does
Flow                       not perform the check.​
                           3a. The blockchain data is unavailable: The system reports that integrity could not be
                           verified.​
                           4a. The hash does not match: The system reports an integrity discrepancy and
                           preserves the existing audit record.


Postconditions             Success: The verification result is displayed as matching or as a discrepancy. The audit
                           record is not modified by verification.


            Field                                                Description

Use Case ID and Name       UC-033 — View Profile


Primary Actor              System Admin
Goal                       View the System Admin's own account profile.


Trigger                    System Admin selects View Profile.


Preconditions              System Admin is logged in.


Main Flow                  1. System Admin opens the profile function.​
                           2. The system retrieves the authenticated administrator's profile.​
                           3. The system displays the available profile information.


Alternative or Exception   2a. The profile cannot be retrieved: The system displays an error and allows System
Flow                       Admin to retry.


Postconditions             Success: The administrator's own profile is displayed. No profile information is changed.




            Field                                                 Description

Use Case ID and Name       UC-034 — View Hospital Location on Map


Primary Actor              Hospital


Goal                       View the hospital's saved location on a map.


Trigger                    Hospital staff select the hospital location map function.


Preconditions              Hospital staff are logged in and the hospital profile contains location information.


Main Flow                  1. Hospital staff open the hospital location map.​
                           2. The system retrieves the location saved in the hospital profile.​
                           3. The system displays the hospital's location on a map.


Alternative or Exception   2a. The hospital profile has no location: The system informs Hospital staff that the
Flow                       location is unavailable.​
                           3a. The map service cannot load: The system displays an error and allows Hospital staff
                           to retry.


Postconditions             Success: The hospital's recorded location is displayed on the map. No profile or location
                           data is changed.
2.6​System Architecture




              Figure 2.8. System Architecture of the Proposed System
CHAPTER 3
SYSTEM DEVELOPMENT
This chapter explains how the approved design was implemented, the methodology used, the
resources required, and the user interface design.


3.1​Development Methodology
Student guidance: Name and justify the methodology used, such as Waterfall, Agile, Scrum, Rapid
Application Development, Prototyping, or an Iterative model.




                       Figure 3.1. Development Methodology Applied to the Project
Explain how each phase or iteration was applied to this project, not only its textbook definition.
3.2​Software and Hardware Requirements
3.2.1​Development Requirements

   Category           Item                 Minimum Specification or Version            Purpose
  Hardware      Developer computer         CPU + GPU: AMD Ryzen AI 9 HX       Development and testing
                                           370 + Radeon 890M (16 CUs,
                                           RDNA 3.5)

                                           RAM: DDR5DDR3 > DDR5 min.
                                           4gb ram up to 16.0 GB of ram

                                           Storage: Fast NVMe SSD (1TB+)
                                           100GB free

                                           Processor: AMD Ryzen 5 3400G
                                           with Radeon Vega Graphics
                                           3.70 GHz

 Software       Operating system           Windows 11                         Development environment

 Software       Programming                React JS/Vite + React, Leaflet +   Application development
                   language or             OpenStreetMap
                    framework

 Software       Database                   Firebase Cloud Firestore           Data storage
                management
                system

 Software       Development tools             1.​   Figma                     Coding and collaboration
                                              2.​   Visual Studio Code
                                              3.​   Draw.io
                                              4.​   Canva
                                              5.​   Github & Git
                                              6.​   Discord
                                       ​




3.2.2​Deployment and User Requirements

     User or      Hardware             Software or Connectivity                  Notes
   Component      Requirement               Requirement
  End user      1. Mobile          Mobile Browser: Google, Safari​            Minimum: 3G, enables
  (Donor&Reci   2.Desktop          Desktop Browser: Google, Safari,           core functions (login,
  pient)                           Microsoft Edge, Mozilla Firefox, Opera,    view/accept requests).
                                   Opera GX                                   Recommended: 4G/LTE,
                                   ​                                          5G, or Wi-Fi required for
                                   Mobile OS: IOS/Android​                    reliable GPS-based
                                   Desktop OS: Windows, Linux, MacOS          matching and real-time
                                                                              map rendering (NFR-01,
                                   Internet: Mobile data (3G/4G/LTE
                                                                              NFR-05).
                                   minimum, 4G/5G preferred) or Wi-Fi
                          (minimum 5 Mbps download / 1 Mbps
                          upload)


End user     Desktop      Desktop Browser: Google, Safari,           Minimum: 5 Mbps
(Hospital)                Microsoft Edge, Mozilla Firefox, Opera,    broadband.
                          Opera GX                                   Recommended: wired
                                                                     connection with backup
                          Desktop OS: Windows, Linux, MacOS​         (mobile hotspot or
                          ​                                          secondary ISP) dropped
                          Internet: Broadband internet               connectivity during an
                          (minimum 5 Mbps download / 1 Mbps          active emergency request
                          upload), wired or Wi-Fi
                                                                     is higher-risk for a hospital
                                                                     than for an individual user.

End user     Desktop      Desktop Browser: Google, Safari,           Minimum: 5 Mbps
(System                   Microsoft Edge, Mozilla Firefox, Opera,    broadband. Admin actions
Admin)                    Opera GX                                   (account management,
                                                                     system configuration) are
                          Desktop OS: Windows, Linux, MacOS​         infrequent but
                          ​                                          higher-impact if
                          Internet: A Stable Broadband internet      interrupted mid-action.
                          (minimum 5 Mbps download / 1 Mbps
                          upload), wired or Wi-Fi

Server or    [CPU, RAM,   Hardware Requirement (CPU, RAM,            Recommended:
hosting      storage]     storage):                                  auto-scaling or load
                                                                     balancing to sustain
                          CPU: 2 vCPUs minimum, 4 vCPUs              NFR-03 (500 concurrent
                          recommended                                users) and NFR-06
                          RAM: 4 GB minimum, 8 GB                    (99.5% uptime).
                          recommended
                          Storage: 50 GB SSD minimum,
                          scalable/expandable as donor and
                          donation records grow

                          Software Requirement (OS, runtime,
                          database):

                          Platform: Firebase
                          Runtime: Node.JS
                          Database: Firebase Cloud Firestore
                          (NoSQL)


                          OS: Linux (e.g., Ubuntu Server LTS)
                          Runtime: your chosen backend
                          framework (e.g., Node.js/Express,
                          Laravel, or Firebase Cloud Functions
                          pick whichever your group is actually
                          building with)
                          Database: a relational database (e.g.,
                          MySQL or PostgreSQL) for donor,
                          recipient, hospital, and request
                          records; plus your blockchain-based
                          audit ledger component (NFR-15) for
                          immutable audit logging
                          Since you're pairing this with a Flutter
                          mobile web app (per your other
                          coursework), Firebase (Firestore +
                          Cloud Functions + Cloud Messaging
                          for notifications) is a common, low-cost
                               pairing worth considering if you haven't
                               picked a stack yet it also gives you
                               push notifications and hosting in one
                               place.

    Peripheral or   [Device]   [Driver or integration]                    N/A for current scope
    special
    device




​
3.3​User Interface Design
Student guidance: Present the major / all screens in the order users normally encounter them. Each figure
should include a readable screenshot and a brief explanation of its purpose. Protect real personal or
confidential data in screenshots.

3.3.1​Interface Screens




                                  Figure 3.2. [Screen Name] Interface
         CHAPTER 4
         TESTING AND EVALUATION
         This chapter provides evidence that the developed system satisfies its documented
         requirements and behaves correctly under expected and invalid conditions.


         4.1​Testing Strategy
         Student guidance: State the testing scope, environment, testers, test data, entry and exit criteria, and
         treatment of defects. At minimum, cover the major functional requirements and important non-functional
         requirements.

                   Testing Item                                             Project Details
          Testing objective             [What the testing aims to verify]

          Test environment              [Hardware, software, browser, device, network, and version]

          Testers                       [Developers, client representatives, intended users, or evaluators]

          Test data                     [Valid, invalid, boundary, and sample data used]

          Entry criteria                [Conditions before testing begins]

          Exit criteria                 [Required pass rate or absence of critical defects]




         4.2​Test Cases and Black Box Testing
         Student guidance: Black-box testing verifies system behavior from inputs and expected outputs
         without examining source code. Include positive cases, negative cases, boundary cases,
         permissions, and error handling. Each test case should trace to a requirement.



  Test    Require           Module or   Precondition      Test Data or Steps          Expected Result         Actual Result      Status
Case      ment ID            Feature
ID
                                                         1.​                [Step]
                                        [Required                                    [Observable                                Pass​      /
TC-01    FR-01            [Feature]                      2.​                [Step]                          [Observed result]
                                        state]                                       expected result]                           Fail
                                                         Data: [value]

                                        [Precondition    [Invalid or boundary        [Expected validation
TC-02    FR-[ ]           [Feature]                                                                         [Actual result]     [Status]
                                        ]                input and steps]            or result]

                          [Quality      [Precondition                                [Measurable
TC-03    NFR-[ ]                                         [Test procedure]                                   [Observed value]    [Status]
                          attribute]    ]                                            criterion]
       4.3​Test Summary
           Module or Requirement       Cases       Passed          Failed      Pass Rate            Remarks
                   Group              Executed
          [Module 1]                [No.]         [No.]        [No.]           [00.00%]      [Summary]

          [Module 2]                [No.]         [No.]        [No.]           [00.00%]      [Summary]

          Overall                   [Total]       [Total]      [Total]         [00.00%]      [Decision]




       4.4​Defect and Revision Log
 Defect       Related         Description           Severity             Corrective Action      Retest Result      Status
   ID          Test
                                                 [Critical​    /                                                [Closed​    /
D-01         TC-[ ]     [Observed problem]                          [Revision made]             [Pass / Fail]
                                                 Major / Minor]                                                 Open]

D-02         TC-[ ]     [Problem]                [Severity]         [Action]                    [Result]        [Status]
CHAPTER 5
CONCLUSION AND RECOMMENDATION
This chapter summarizes what the project accomplished, states evidence-based conclusions,
and proposes practical improvements or next steps.


5.1​Conclusion
Student guidance: Answer the project objectives using evidence from the completed analysis, developed
system, and test or evaluation results. Do not introduce new results. State what was achieved, what the
evidence supports, and what remains subject to the stated limitations.

[ Write a concise synthesis of the problem addressed, solution developed, major verified capabilities,
and overall project outcome. ]




5.2​Recommendations
Student guidance: Give specific and feasible recommendations based on the findings, limitations, failed or
deferred test cases, user feedback, and future operational needs.
REFERENCES
Student guidance: List every source cited in the document using the citation style required by the
instructor. Include policies, technical documentation, scholarly sources, and organizational documents
when applicable.

[ [Author or Organization. (Year). Title. Publisher or source. URL or DOI, when applicable.] ]




APPENDICES
Student guidance: Include supporting material that is too detailed for the main chapters. Refer to every
appendix in the main text and protect confidential or personally identifiable information.
FINAL SUBMISSION CHECKLIST
☐​   All bracketed prompts and unused sample rows have been removed.
☐​   The objectives, requirements, diagrams, interface designs, and test cases are aligned.
☐​   DFD levels are balanced, and all data flows are clearly named.
☐​   The ERD includes keys, relationships, and cardinalities, and matches the data dictionary.
☐​   Every major functional requirement has at least one test case.
☐​   Figures and tables are readable, numbered, captioned, and discussed in the text.
☐​   Sensitive information has been removed or anonymized.
☐​   References and in-text citations use one consistent style.
☐​   Include a table of contents.
