#Defensive 
### What Is STIX?

STIX is a language for having a standardized communication for the representation of cyberthreat information. Similar to TAXII, it is not a sharing program or tool, but rather a component that supports programs or tools. The STIX language has a number of constructs or components, including the following:

- **Observable:** A dynamic event or stateful property, represented in CybOX.
- **Indicator:** An observable with context. An indicator can contain a time range, information source, intrusion detection system rules, etc.
- **Incident:** A set of activity associated with the same adversary along with context.
- **Tactics, Techniques and Procedures (TTP):** Represents the modus operandi of the adversary.
- **Exploit Target:** A weakness of a victim in light of a TTP.
- **Course of Action (COA):** Defensive actions against a threat (prevention, remediation, mitigation).
- **Campaign:** A set of related TTPs, indicators, incidents and exploit targets.
- **Threat Actor:** The cyber adversary.

One of the things that sometimes causes confusion with STIX constructs is whether to use incident or indicator. If you are aiming to provide a history for further analysis or follow-up, you have to use an incident construct. If you want to build a list of items to look for, use an indicator construct.