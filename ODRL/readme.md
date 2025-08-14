# ODRL in Research Data Licenses

This repository holds work on the development of ODRL expressions of research data sharing agreements.

## ODRL references
- [ODRL Model](https://www.w3.org/TR/odrl-model/)
- [ODRL Vocabulary](https://www.w3.org/TR/odrl-vocab/)
- [ODRL Best Practices](https://www.w3.org/community/reports/odrl/CG-FINAL-profile-bp-20240808.html)

# Introduction to Working with ODRL

The **Open Digital Rights Language (ODRL)** is a standard way to describe rules about how digital content and services can be used.  
With ODRL, you can express:

- **Permissions** – what’s allowed.
- **Prohibitions** – what’s not allowed.
- **Obligations** – what must be done.

These rules can also be refined with **constraints** (e.g., time limits or location restrictions) and **duties** that must be fulfilled.


## The Building Blocks: Policies and Rules

At the heart of ODRL is the **Policy**.  
A Policy is a container that holds one or more **Rules**. Each Rule can be a:

- **Permission** – an action someone is allowed to take.  
- **Prohibition** – an action that is not allowed.  
- **Duty** – something that must be done.

ODRL is flexible: a Policy can be very detailed, or it can be minimal, depending on your needs.


## Atomic Rules: The Most Basic Form

While a Policy may combine multiple elements, the ODRL Information Model defines an **“atomic” Rule** — the smallest form of a Rule that can’t be broken down further.  

An atomic Rule usually relates to:

1. **One Asset** – the thing the rule applies to (e.g., a dataset, an image, a collection of files).  
2. **One or more Parties with functional roles** – the people or organisations involved (e.g., the assigner, the assignee).  
3. **One Action** – what is being done with the Asset (e.g., `use`, `copy`, `modify`).  
4. **Optional Constraints or Duties** – extra conditions or requirements for that single Rule.

When policies are written in a more **compact** way (with multiple assets, parties, or actions in one rule), they should still be processed into these atomic rules for compliance and clarity.

## Policy Metadata and Context

Before listing its Rules, a Policy often contains **metadata** — information about the policy itself. These are properties of the **Policy class**:

- **`@context`** – (in JSON-LD form) links short names to their full identifiers, ensuring the policy is understood by systems reading it.  
- **`@type`** – the type of policy:
  - **Set** – a generic collection of rules (default type).  
  - **Offer** – rules being proposed, not yet granted (must have an assigner).  
  - **Agreement** – rules formally granted between parties (must have both assigner and assignee).  
- **`uid`** – a unique identifier (IRI) for the policy.  
- **`profile`** – identifies the ODRL profile(s) the policy follows, especially if it uses extra terms beyond the ODRL Core Vocabulary.  
- **`inheritFrom`** – points to other policies whose rules and properties are inherited.  
- **`conflict`** – tells what to do if rules in the policy contradict each other:
  - **perm** – permissions win over prohibitions.  
  - **prohibit** – prohibitions win over permissions.  
  - **invalid** – the whole policy is void if there’s a conflict (default).

## Shared Properties in Compact Policies

In some cases, properties that apply to **every Rule** in the policy can be written once at the **Policy level** instead of repeating them in each Rule.  

These aren’t truly “policy-level” in meaning — they’re simply copied into each atomic rule when processed.  

## In Summary

ODRL provides a structured way to say:

> **Who** can do **what**, with **which resources**, under **what conditions**.

By breaking rules into **atomic form** and clearly defining the **metadata** at the policy level, ODRL makes it possible for both humans and machines to interpret usage rights consistently.
