# DANCE agenda:

* Chairs Introduction - 10m

Note Well
Note takers: Tim Wicinski with tale backup

* Use case presentations - 40m
    - TLSA use case for DNS - Bill Woodcock - 10m
    - (https://datatracker.ietf.org/meeting/112/materials/slides-112-dance-use-cases-for-dane-and-bidirectional-tls-authentication-in-the-dns-00)

Viktor Dukhovni: using DANE TLSA for ongoing maint

dkg: Didn't understand "maintenance".  Please clarify.

VD: folks publish TLSA and don't keep correct. 

dkg: Use Cases. Not convinced client auth is required. Think on non-client authenication. Why is this "the" Use Case

Wes: Intent isn't really to establish this as "the" Use Case but one of several to be thinking about

BW: blinded certs not tied to identities.

(From Jabber:
    dkg: is it a design goal here to include role authentication and blinded certs?
    Wes: it's a design goal to build a flexible framework that can enable multiple future forward paths with the resulting technology. It's not within scope to select individual ones and DANCE outputs would map to them now.)

    - Device-to-cloud - Ash Wilson - 10m
    - https://datatracker.ietf.org/meeting/112/materials/slides-112-dance-dance-https-00.pdf

Ben Schwartz: client ship complete DANE cert chain? 

WH: So you mean sending all DNSKEYs and RRSIGS up to the root?

BS: Client should not have to do any network to validate.  Should not cache anything

VD: Agree with Ben but maybe optional

Shumon Huque: TLS chain extension can do this, configure to go the other way. (RFC 9102)

    - EAP-TLS use case - Ash Wilson - 10m
    - https://datatracker.ietf.org/meeting/112/materials/slides-112-dance-dance-eap-tls-00.pdf

dkg: How client selecting which identity to present to the network?

AW: For many IoT devices they'll only be able to have one identity to present.  Will have to think more for the generalized user case.

(Ben, in Jabber: I think IoT is not a good use case for DANCE until we have a "re-provisioning" system so the owner can change the name of the device.)

Viktor:  skeptical of this use case (edit note: which one? What is "this" [chair: I believe he meant EAP/clients at all])


* Architecture document presentations - Ash Wilson - 30m
    - https://www.ietf.org/archive/id/draft-wilson-dance-architecture-00.txt
    - https://datatracker.ietf.org/meeting/112/materials/slides-112-dance-dance-architecture-01.pdf

Shumon: SMTP Client use case absent. 

Viktor: SMTP client is MTA. MTA<->MTA work hard to be identified as legitimate. Audit trails and reputation. 
One thing we are not talking about cred exchange - start with DNS, once authenicated, switch to something else?
Wow on interesting Kerberos scale - must go to recordings. 

Bob Moskowitz (chat): BTW, I am looking at this approach for DRIP's unmanned aircraft certs that are behind the whole HHIT methodology. Aviation is/has built a bridged PKI (on my bridge PKI model from back in '98), but I have gotten their CP to include federated PKI. So by putting UA certs in DANCE/DANE format and federating this to the IATF I meet the ICAO goals and mine.


Paul Muchene: question on scalability. possibility of fallback solution? 

Ash: up for discussion. Fallback mode useful

Viktor: fallback sounds like using DANE for enrollment. 

* Solution documents - Shumon Huque - 30m
    - https://datatracker.ietf.org/doc/html/draft-huque-dane-client-cert
    - https://datatracker.ietf.org/doc/html/draft-huque-tls-dane-clientid
    - https://datatracker.ietf.org/meeting/112/materials/slides-112-dance-dane-tls-client-authentication-00.pdf

Wes, relaying from chat, that client IDs (especially IOT) is privacy-leaking.  Should we use just TLS 1.3 and skip 1.2?

dkg: Client Hello marked with DANE client ID? 

Shumon: Not in first request...

dkg: no need for extension if you know client id is visible, let server figure it out. 

Ben from jabber:  it is request-response, but in the opposite direction

Robin Wilton (chat):  relevant also to Viktor's previous comment about scalability: 
if you want to use DANE for the enrolment request/reply but not for every subsequent connection request, 
don't you need this kind of "bootstrapping" step in the protocol?

dkg: what we really need is just a way to identify that a cert is a dane cert

Roman: Can we go to TLS1.3 only but check use cases, thought we were using greenfield.

Ben: 

Shumon: something must regenerate the chain

Ben: shipping a chain servers can require (profile)

Viktor: client needs to regenerate to send a chain. most essential is RRSIG of TLSA record. 
Validity at most 4 weeks. could be embedded in existing chains(?). 

Viktor: could use OID for specifying name space within TLS certificates
 - The server presents a list of valid CAs, which could be used to select a client credential - providing the CA identifier can point to a DANE entrypoint

Olle super hard to hear, but was trying to make a point about discussing namespaces with dnsop?  In Jabber clarified: The DNS namespace needs to be discussed so that we build a tree instead of a flat name space We have a potential for very large amount of clients, especially in the IOT space



* ...
* AOB and closing - 10m

Poll to adopt both solution docs.
    raise hands: 20
    don't raise hands: 1
    total participants: 21

dkg: wants to hear why docs are not ready from one person
- No one voiced opinions about being against

# How to DANCE:
- general info: https://datatracker.ietf.org/wg/dance/about/
- meeting materials: https://datatracker.ietf.org/meeting/112/session/dance
- mailing list: https://www.ietf.org/mailman/listinfo/dance
