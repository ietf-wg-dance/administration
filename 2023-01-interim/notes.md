## Templates Document

- similar to how ROLL does templates
    - https://github.com/ietf-wg-dance/draft-ietf-dance-dancing-template/blob/main/draft-johansson-dance-template.md
    - https://github.com/ietf-wg-dance/draft-ietf-dance-dancing-template/
- fill in the blank sections that 
- question to the group: what should go into the template?
- Rick van Rein: what are you templating?
    - The architecture document will describe how to DANCE in general
    - Some protocol documents will describe TLS
    - This will define how to do DANCE with protocol specific dancing instructions (SMTP, etc)
    - can use the document to creat documents about using DANE clients with various protocols
- why only in a draft form -- why not in an RFC?
    - for IANA registrations it's a bit easier and an RFC could publish it
    - this is a bit different in order to make dancing documents similar in structure
    - should pre-list security questions that secdir reviews might be asking, eg
- who has preference for one way or another?
    - Shumon: should be published somewhere
    - appendix to architecture or somewhere permenently?
- Olle: could postpone this decision until it gets closer to architecture publication
- choices essentially:
    1. publish as an RFC
    2. publish as a WG-adopted internet draft that never goes to RFC
    3. publish just as an ID
- DECISION: postpone this decision for now

## Architecture document

- significantly revamped lots of the architecture document
- focus on use cases that are interesting
- non-goal: covering all use cases
    - template should fill this roll
- authors specifically want to move some items out of the architecture document:
- oauth2?
    - issue #6 in document
    - Rick will look at the OAUTH2 use case
    - oauth2 likely to be dropped
- DNS over client TLS authentication?
    - issue #7
- discussion over whether special items should go into the architecture document vs a separate RFC
    - proposal is to move some of these to a future work item list
    - things in the architecture document should be base frameworks (authid looks like an email address, etc)
- StartTLS SMTP
    - issue #8
    - Viktor Dukhovni has said in the past (but is not present today)
    - SMTP clients can benefit from DANCE
    - especially for submission
- Anomaly reporting
    - issue #14
    - MUD and XARF reporting
    - some details in ticket
    - XARF is a transport for reporting abuse
    - document signing not TLS
    - will defer this to future work
- Terminology
    - issue #28
    - do we need more terminology?
    - pull in terminology from other documents and include in architecture
    - include any other terminology that needs to be relevant
    - shouldn't be a long list
- upcoming 116 agenda items
    - 1hr
    - update on architecture document
    - start at implementation document?
    - update from Rick on oauth2
    - update from Viktor on SMTP
    - update on template document
    - Michael will DANCE publicly
