---
title: "Project Details"
teaching: 15
exercises: 0
questions:
- "How will the group projects work?"
- "What is the project you will be working on?"
objectives:
- "Explain the background and the project you will be doing for the next 3 days."
- "How each group will work together."
- "Assessment deliverables"
keypoints:
- "The groups will be identical to the SABS year-long open source software groups." 
- "Project management will consist of (at least) daily stand-ups and the use of GitHub 
  issues and pull requests."
- "Submit your GitHub repository for assessment by 5:30pm Friday 23rd September."
---

# Pharmokinetic Modelling

The field of Pharmokinetics (PK) provides a quantitative basis for describing the 
delivery of a drug to a patient, the diffusion of that drug through the plasma/body 
tissue, and the subsequent clearence of the drug from the patient's system. PK is used 
to ensure that there is sufficient concentration of the drug to maintain the required 
effecicy of the drug, while ensuring that the concentration levels remain below the 
toxic threshold (See Fig 1). Pharmokinetic (PK) models are often combined with 
Pharmodynamic (PD) models, which model the positive effects of the drug, such as the 
binding of a drug to the biological target, and/or undesirable side effects, to form a 
full PKPD model of the drug-body interaction. This project will only focus on PK, 
neglecting the interaction with a PD model.

PK enables the following processes to be quantified:

- Absorption
- Distribution
- Metabolism
- Excretion

These are often referred to as ADME, and taken together discribe the drug concentration 
in the body when medicine is prescribed. These ADME processes are typically described by 
zeroth-order or first-order *rate* reactions modelling the dynamics of the quantity of 
drug $q$, with a given rate parameter $k$, for example:

$$\frac{dq}{dt} = -k^*,$$
$$\frac{dq}{dt} = -k q.$$

The body itself is modelled as one or more *compartments*, each of which is defined as a 
kinetically homogenous unit (these compartments do not relate to specific organs in the 
body, unlike Physiologically based pharmacokinetic, PBPK, modeling). There is typically 
a main *central* compartment into which the drug is administered and from which the drug 
is excreated from the body, combined with zero or more *peripheral* compartments to 
which the drug can be distributed to/from the central compartment (See Fig 2). Each 
peripheral compartments is only connected to the central compartment.

The following example PK model describes the two-compartment model shown diagramatically 
in Fig 2. The time-dependent variables to be solved are the drug quantity in the central 
and peripheral compartments, $q_c$ and $q_{p1}$ (units: [ng]) respectivly.

$$
\frac{dq_c}{dt} = \text{Dose}(t) - \frac{q_c}{V_c} CL 
- Q_{p1} \left ( \frac{q_c}{V_c} - \frac{q_{p1}}{V_{p1}} \right ),
$$

$$
\frac{dq_{p1}}{dt} =  Q_{p1} \left ( \frac{q_c}{V_c} - \frac{q_{p1}}{V_{p1}} \right ).
$$

This model could describes an intravenious bolus dosing protocol, with a linear 
clearence from the central compartment (non-linear clearence processes are also 
possible, but not considered here). The input paramters to the model are:
- The dose function $\text{Dose}(t)$, which could consist of instantaneous doses of $X$ 
  ng of the drug at one or more time points, or a steady application of $X$ ng per hour 
  over a given time period.
- $V_c$ [mL], the volume of the central compartment
- $V_{p1}$ [mL], the volume of the first peripheral compartment
- $V_{p1}$ [mL], the volume of the peripheral compartment 1
- $CL$ [mL/h], the clearance/elimination rate from the central compartment
- $Q_{p1}$ [mL/h], the transition rate between central compartment and peripheral 
  compartment 1

Another example model we will show uses subcutaneous dosing, and adds an additional 
compartment from which the drug is absorbed to the central compartment:

$$
\frac{dq_0}{dt} = \text{Dose}(t) - k_a q_0,
$$

$$
\frac{dq_c}{dt} = k_a q_0  - \frac{q_c}{V_c} CL 
- Q_{p1} \left ( \frac{q_c}{V_c} - \frac{q_{p1}}{V_{p1}} \right ),
$$

$$
\frac{dq_{p1}}{dt} =  Q_{p1} \left ( \frac{q_c}{V_c} - \frac{q_{p1}}{V_{p1}} \right ),
$$

where $k_a$ [/h] is the “absorption” rate for the s.c dosing.





{% include links.md %}

