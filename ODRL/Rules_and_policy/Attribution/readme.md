# Background information

## Attribution in ODRL

**ODRL (Open Digital Rights Language)** supports attribution by providing specific actions and party functions that can be used **directly** within policy rules (such as Permissions or Prohibitions), without necessarily requiring a separate Duty.

---

### How Attribution is Supported

#### `attribute` Action
- ODRL includes a defined action called **`attribute`**.
- Meaning: *"To attribute the use of the Asset"*.
- Can be applied directly to an asset within a rule.

#### Attribution Party Functions
To specify **who should be attributed** or **who is responsible for attributing**, ODRL provides specific party functions (sub-properties of the abstract `function` property):

- **`attributedParty`**  
  The party to be attributed (person, organisation, etc.) — the entity receiving credit or acknowledgment.

- **`attributingParty`**  
  The party responsible for performing the act of attribution.

---

### Attribution Without a Duty

While attribution can be expressed as a **Duty** (an obligation to perform an action), it is **not limited to this**.  
The `attribute` action can be **directly associated** with a Permission, meaning:

- A party is permitted to use an asset **if they also fulfill the attribution requirement**.
- `attributedParty` and `attributingParty` can be specified within the Permission to define who is credited and who does the attribution.

---

### Example: Attribution as Part of a Permission

**Scenario**: A policy grants permission to distribute a photograph, but requires attribution to the original photographer.

```json
{
  "@context": "http://www.w3.org/ns/odrl.jsonld",
  "@type": "Policy",
  "uid": "http://example.com/policy:PhotoAttribution",
  "permission": [{
    "target": "http://example.com/asset:MyGreatPhoto.jpg",
    "action": "distribute",
    "assigner": "http://example.com/photographer:JaneDoe",
    "assignee": "http://example.com/publisher:GlobalNews",
    "action": "attribute",
    "attributedParty": "http://example.com/photographer:JaneDoe"
  }]
}
```
### Explanation of the Example

- @type: Policy (defaults to Set if no other type is specified).
- uid: Unique identifier for the policy.
- target: The asset in question (http://example.com/asset:MyGreatPhoto.jpg).
-  action: distribute: Grants the right to distribute the asset.
-  assigner / assignee: Defines the parties granting and receiving the permission.
-  action: attribute: Specifies the attribution requirement.
-  attributedParty: Identifies who must be credited (JaneDoe).

