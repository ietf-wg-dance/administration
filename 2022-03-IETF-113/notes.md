# Meeting information

    Friday, March 25, 2022 -- 10:00-12:00 (09:00-11:00 UTC)

    Room: Park Suite 8

    Notes: https://notes.ietf.org/notes-ietf-113-dance
    
    YouTube: https://www.youtube.com/watch?v=tWLNi_UkmS8

# DANCE agenda:

##    10m - Chairs Introduction (Joey and Wes)
        WG activity level
        Adoption call results and discussion
            Including TLS WG coordination
            
##    20m - Hackathon implementation results (Gaël and Sanoche)

Worked on both drafts during the hackathon (client-cert and tls-dane-clientid)

dane-client-cert:
  - Used a go library for DANA TLSA Auth (via shumon)
  - Auth based on dane_clientid, fallback to SAN when not sent

tls-dane-clientid:
  - extending tls 1.2 and 1.3 to use new extension dane_clientid
  - added dane_clientid support for the TLS handshake
  - outstanding question: should this extension be used in both 1.2
    and 1.3 in the same way?

    Shumon Huque: they should be the same, but slightly different needed to encrypt

    Hannes Tschofenig: Could send an empty extension in the client
    hello to indicate future extensions may be coming

  - key sharing and onboarding described

  - currently end-to-end security not possible

    Hannes: it is still possible, but keys can be fragmented with
    slower transmission

  - Described how adding multiple client IDs via DANE has been made
    significantly easier

  - Question from Hannes: Is the communication between TLS network
    server and trunk server?    

    Answer: Between network server and joint server.

  - Question from Shumon: was necessary to fork Go TLS library ? 

    Gael: yes

    Hannes: unavoidable to include extensions into the core

## 20m - Architecture (Olle Johanss)

Hannes: I suggest splitting the document into parts

Wes: Use case examples are potentially a good way to break this
document up. If folks feel arch document is ready to go, can do so.

Barry Leiba:  Why do we think doc needs to be ready to be adopted?

    40m - Solution documents (Shumon Huque)



    20m - Open mic
    
    10m - Closing and Next Steps (Joey and Wes)

