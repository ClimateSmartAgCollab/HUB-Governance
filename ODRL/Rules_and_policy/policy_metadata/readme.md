## Policy Metadata in ODRL

In the **Open Digital Rights Language (ODRL) Information Model**, *policy metadata* refers to the information that appears **before the rule definitions** in an atomic ODRL expression.  
These metadata elements are **properties of the Policy class**, sometimes called **Policy-level properties**.

---

### Common Policy-Level Properties

#### `@context`
- **Purpose**: In JSON-LD serialisations, defines the processing context.  
- **Function**: Maps short-form aliases of concept identifiers to their full identifiers.  
- **Importance**: Essential for expressing ODRL policies in JSON-LD.

#### `@type`
- **Purpose**: Identifies the specific Policy subclass being used.  
- **Values**:
  - `Set` – a generic collection of rules (**default** if not specified).  
  - `Offer` – rules being proposed but not yet granted (must include an assigner).  
  - `Agreement` – rules formally granted (must include both assigner and assignee).

#### `uid` (Unique Identifier)
- **Requirement**: Every Policy **MUST** have exactly one `uid` property value of type IRI.  
- **Purpose**: Uniquely identifies the policy.

#### `profile`
- **Purpose**: Identifies the ODRL Profile(s) the policy follows.  
- **Usage**: **MUST** be included if the policy uses terms from an ODRL Profile beyond the ODRL Core Vocabulary.  
- **Type**: IRI.

#### `inheritFrom`
- **Purpose**: Points to parent policies from which this policy inherits:
  - All atomic Rules.
  - Shared policy-level properties.  
- **Type**: IRI.

#### `conflict`
- **Purpose**: Specifies how to handle rule conflicts.  
- **Possible Values**:
  - `perm` – Permissions override Prohibitions.  
  - `prohibit` – Prohibitions override Permissions.  
  - `invalid` – Entire policy is void if conflicts are detected (**default** if not set).
