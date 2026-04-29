# The SKIDS Tier System

The SKIDS clinical service catalogue is organised into three tiers. This
document defines each tier, the qualification framework, and the
operational implications.

---

## The framework

A pediatric clinical service qualifies as a SKIDS specialty clinic if and
only if all of these are true:

```
1. IAP / AAP / standard pediatric texts endorse OPD management
2. There is a defined diagnostic protocol (history + exam + scale + test)
3. There is a POC / OPD-housable diagnostic device, or no device beyond exam
4. There is an evidence-based therapeutic that can be dispensed in-clinic
5. There is a defined follow-up / monitoring schedule
6. The unit economics make sense at realistic patient flow
```

If a service fails any of those six tests for primary care, the question
becomes: who delivers it?

```
Can a general MD-Paeds deliver it under a tight protocol with safe
referral triggers?

  YES → Tier 1 (every SKIDS pediatrician delivers from day one)
  NO, requires named subspecialty credential → Tier 2
  NO, requires procedural / surgical capability → Tier 3 (partner referral)
```

The boundary between Tier 1 and Tier 2 is the central design decision of
the SKIDS clinical platform. Get it right and the platform is broad,
defensible, and scalable. Get it wrong and SKIDS either becomes too
narrow (refers everything beyond well-baby visits) or unsafe (treats
things it shouldn't).

---

## Tier 1 — every SKIDS pediatrician delivers under protocol

The SKIDS pediatrician runs these directly using:
- A SKIDS Protocol (this library)
- An in-clinic diagnostic device
- An in-clinic therapeutic dispensary
- Allied staff (audiologist, optometrist, dietitian, counsellor, etc.)

A credentialed subspecialist provides **protocol governance** —
quarterly case-review, protocol updates, edge-case consultation —
not personal delivery.

### Tier 1 services (23 total)

```
A1   SKIDS Screening                  (the front door)

B1-01  Vision Clinic                  Welch Allyn Spot Vision · spectacles · myopia control
B1-02  Hearing & Ear Clinic           SoundScout · cerumen removal · AOM/OME mgmt
B1-03  Throat & Airway Clinic         RADT · pharyngitis · tonsillitis medical · croup
B1-04  Oral Health Clinic             caries screen · fluoride varnish · SDF · hygiene kit
B1-05  Skin Clinic                    eczema · acne · scabies · derm topicals dispensed
B1-06  Allergy Clinic                 SPT · spirometry · GINA stepwise · adrenaline kits
B1-07  Sleep Clinic                   BEARS/PSQ · sleep hygiene · oximetry loaner
B1-08  Behavioural Clinic             M-CHAT-R · Vanderbilt · CBCL · LISSUN partnership
B1-09  Nutrition & Growth Clinic      BIA · growth · iron/D dispensed · meal plans
B1-10  Obesity & Metabolic Clinic     BMI percentile · BIA · 12-week lifestyle programme
B1-11  Speech & Language Clinic       REELS · DEAP · in-clinic SLT sessions
B1-12  Learning Clinic                DST-J · NIMHANS · remediation · school liaison
B1-13  Adolescent Clinic              HEEADSSS · Tanner · contraception · STI
B1-14  Pulmonology / Asthma Clinic    spirometry · GINA 1-4 · action plans
B1-15  Gastrointestinal Clinic        Rome IV · GORD · constipation · CMPA elimination
B1-16  Cardiac Clinic                 AyuSynk · ECG · innocent murmur · sports clearance
B1-17  Kidney & Urology Clinic        UA · BP · UTI workup · enuresis · proteinuria
B1-18  Blood Clinic                   IDA · thalassemia trait · stable SCD · ITP follow-up
B1-19  Infections Clinic              recurrent infection w/u · TB screen · travel · PEP
B1-20  Bedwetting Clinic              voiding diary · alarm · desmopressin
B1-21  Constipation Clinic            Rome IV · disimpaction · macrogol maintenance
B1-22  Vaccination Clinic             IAP IIS · catch-up · adolescent · travel
B1-23  Developmental Surveillance     Trivandrum DST · ASQ-3 · CDC milestones
```

### Tier 1 protocol governance

Every Tier 1 protocol has a named **protocol owner** — a credentialed
subspecialist who:
- signs off on §2, §5, §7 (the clinically sensitive sections)
- conducts quarterly case-review of a sample of cases run under the protocol
- updates the protocol when guidelines change
- consults on edge cases the SKIDS pediatrician escalates

The protocol owner is named in §2 of each protocol and in §12 quality
and audit. They may be:
- a SKIDS pediatrician with the relevant subspecialty credential
- an external subspecialist contracted as a SKIDS consultant
- a partner-network subspecialist with whom SKIDS has formal governance ties

---

## Tier 2 — Fellowship-credentialed pediatrician required

These services genuinely require a pediatrician with formal subspecialty
training. Protocol alone cannot substitute for credential. The therapeutic
indices are too narrow, the failure modes too severe, the diagnostic
interpretation too complex for safe delivery without subspecialty mastery.

### Tier 2 services (3 total)

```
B2-01  Endocrine Clinic       T1DM · GH therapy · CAH · GnRH analogues · DSDs
B2-02  Neurology Clinic       epilepsy initiation/titration · neurodegenerative
B2-03  Rheumatology Clinic    DMARDs · biologics · uveitis screening interpretation
```

### Why only three?

Most subspecialty-named services in pediatrics actually have a primary-tier
that any pediatrician can deliver under protocol — and a complex tier that
requires the credential. The Tier 1 list above already captures the primary
tier of allergy, sleep, dermatology, pulmonology, GI, cardiology, nephrology,
hematology, ID, and more.

Endocrine, neurology, and rheumatology are different. Their primary tiers
already involve high-stakes pharmacotherapy with narrow therapeutic indices.
There is no safe "primary tier" for insulin titration, anti-epileptic
selection, or methotrexate management. The credential is non-negotiable.

### Tier 2 activation in a SKIDS clinic

A SKIDS clinic activates a Tier 2 service when one of its pediatricians
holds the relevant credential — either by joining SKIDS already
credentialed, or by completing The SKIDS Fellowship at a partner
institution.

A SKIDS clinic without an Endocrine-credentialed pediatrician does not
run an Endocrine Clinic. It refers Endocrine cases to a partner clinic
in the SKIDS network that does, or to a Tier 3 partnership.

This is honest. Marketing must reflect operational reality, not aspiration.

---

## Tier 3 — partnership / referral, leads given by SKIDS

Services that require expertise SKIDS should not absorb in-house but
where SKIDS captures clear orchestration value as the trusted referrer
and patient flow generator.

### Tier 3 partnerships (7 pathways)

```
Pedodontist            restoration · orthodontics · surgical dental work
ENT surgeon            tonsillectomy · adenoidectomy · grommets · cochlear
Pediatric ophtha       strabismus surgery · cataract · retinal disease
Pediatric surgeon      hernia · hydrocele · undescended testis · circumcision
Pediatric ortho        bracing · complex deformity · post-trauma surgical
Pediatric oncology     tertiary care · solid tumours · haem malignancies
Pediatric ICU          hospital-based critical care
```

### What SKIDS still owns at Tier 3

Even at Tier 3, SKIDS captures meaningful clinical and commercial value as:
- The screener that identifies the condition early
- The orchestrator that manages the referral with clean handoff
- The longitudinal care coordinator before, during, and after specialist work
- The dispenser of supportive medications and follow-up therapeutics
- The trusted relationship the family returns to for ongoing pediatric care

### Naming partners

Each SKIDS clinic names its specific Tier 3 partners. The protocol's
§7.1, §7.2, §7.3 hard referral triggers reference these named partners
by role; the SKIDS clinic operations document maps role → specific
partner clinic / hospital.

---

## Operational implications

### A new SKIDS clinic on day one

Activates all 23 Tier 1 services using the protocol library, the device
kit, the dispensary stock list, and the allied staff hires. Patient panel
on day one already has access to a more complete pediatric specialty
catalogue than most established generalist clinics.

Tier 2 services come online as credentialed pediatricians join or earn
credentials through The SKIDS Fellowship.

Tier 3 partnerships are negotiated and formalised before clinic launch.

### A SKIDS clinic at full activation

Runs 23 Tier 1 services + 1–3 Tier 2 services + 7 Tier 3 referral
pathways = 30+ specialty pathways under one roof, with a single
longitudinal PHR per child.

### Marketing constraint

The parent-facing marketing for any SKIDS clinic must accurately reflect:
- Which Tier 2 services are live at this specific clinic (named
  pediatrician with credential)
- Which Tier 3 partnerships are in place (named partner)

Generic claims like "endocrine care available at SKIDS" are not
permitted unless every SKIDS clinic actually has an Endocrine Clinic.
Specific claims like "SKIDS Bangalore Endocrine Clinic, run by Dr. X,
DM Pediatric Endocrinology" are encouraged.

### Investor framing

The platform thesis: 23 services live on day one + a clear, scholarship-
funded pathway to add Tier 2 credentialed services + 7 high-volume
Tier 3 referral partnerships. This is structurally larger than any
generalist pediatric clinic chain in India.

---

## Tier discipline rules

Three rules that must hold:

1. **Tier 1 services do not silently become Tier 2.** If a complex case
   in a Tier 1 service exceeds the protocol's scope, the protocol's §7
   hard referral fires. The Tier 1 protocol does not get amended to
   absorb the complex case.

2. **Tier 2 services do not silently become Tier 1.** A SKIDS pediatrician
   without the credential does not start running an Endocrine Clinic
   "informally." Either the credential is earned and the service activates,
   or the case routes to a partner.

3. **Tier 3 services are not absorbed in-house without the formal
   credential and infrastructure.** SKIDS does not start doing dental
   restorations because a parent asked. It refers to the named pedodontist
   partner.

These rules are what keep the platform safe, defensible, and scalable.
