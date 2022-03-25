Meeting information

    Friday, March 25, 2022 -- 10:00-12:00 (09:00-11:00 UTC)

    Room: Park Suite 8

    Virtual: https://meetings.conf.meetecho.com/ietf113/?group=dance&short=&item=1
    Notes: https://notes.ietf.org/notes-ietf-113-dance

DANCE agenda:

    10m - Chairs Introduction (Joey and Wes)
        WG activity level
        Adoption call results and discussion
            Including TLS WG coordination
            
    20m - Hackathon implementation results (Gaël and Sanoche)

Worked on both 

dane-client-cert:
  - used go library for DANA TLSA Auth (via shumon)
  - auth based on dane_clientid, fallback to SAN when not sent
  - 

tls-dane-clientid:
  - extending tls 1.2 and 1.3 to use new extension dane_clientid
  - added dane_clientid support for handshake

Shumon Huque: they should be the same, but slightly different needed to encrypt

Hannes Tschofenig: Could send the extension in the client hello

Hannes: keys can be fragmented, but slow

Hannes: TLS network server and trunk server. Discussion on roaming with DANE client

Shumon: was necessary to fork Go TLS library ? 

Gael: yes

Hannes: unavoidable to include extensions into the core

    20m - Architecture (Olle Johanss)

Hannes: split the document into parts

Wes: use case examples are good ways to break this up. if folks feel arch document is ready to go,
can do so.

Barry Leiba:  why do we think doc needs to be ready to be adopted. 



    40m - Solution documents (Shumon Huque)



    20m - Open mic
    
    10m - Closing and Next Steps (Joey and Wes)

