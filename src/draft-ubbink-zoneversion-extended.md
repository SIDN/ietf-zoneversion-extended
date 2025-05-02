%%%
title = "DNS Zone Version (ZONEVERSION) Extended"
abbrev = "zonever-ext"
area = "Internet"
workgroup = "DNSOP"

[seriesInfo]
status = "standard"
name = "Internet-Draft"
value = "draft-ubbink-zoneversion-extended-00"
stream = "IETF"

date = 2025-05-02T07:00:00Z

[[author]]
initials = "S.W.J."
surname = "Ubbink"
fullname = "Stefan Ubbink"
organization = "SIDN"
[author.address]
 email = "stefan.ubbink@sidn.nl"
 ui = "https://sidn.nl"
%%%

.# Abstract

The DNS Zone Version (ZONEVERSION) extended is a way to get information about
the version of a DNS in the backend.
For example when a DNSSEC signer for a zone generates a new SOA serial, because
it has created new RRSIG records, the original data has not changed, but this
is not visible to anyone looking at the zone. This document will make it
possible show the zone information which is the base of the presented data.


{mainmatter}

# Discussion Venues

This note is to be removed before publishing as an RFC.

Source for this draft and an issue tracker can be found at
https://github.com/SIDN/ietf-zoneversion-extended.git .

# Introduction

The DNS Zone Version (ZONEVERSION [@RFC9660]) extended is a way to get
information about the version of a DNS in the backend.
For example when a DNSSEC signer for a zone generates a new SOA serial, because
it has created new RRSIG records, the original data has not changed, but this
is not visible to anyone looking at the zone. This document will make it
possible show the zone information which is the base of the presented data.

# Terminology and Definitions {#terminology}

The key words "**MUST**", "**MUST NOT**", "**REQUIRED**",
"**SHALL**", "**SHALL NOT**", "**SHOULD**", "**SHOULD NOT**",
"**RECOMMENDED**", "**NOT RECOMMENDED**", "**MAY**", and
"**OPTIONAL**" in this document are to be interpreted as described in
BCP 14 [@!RFC2119;@!RFC8174] when, and only when, they appear in all
capitals, as shown here.

# Relation to the ZONEVERSION option

This document extends the original DNS Zone version Option [!@RFC9660] to
include an extra ZONEVERSION type.

# The backend serial in the zone

To make the backend serial available in the ZONEVERSION, it must be available
in the zone itself. Because creating an out of bound solution would be to much
work.
This document defines a label where the backend serial will be available to be used in the ZONEVERSION.

The backend serial will be published in a \_version label under the zone apex.

For example:

    _version.example.nl IN TXT "2025101099"

There **MUST** only be one \_version label.

# The backend serial ZONEVERSION type

This document defines a new ZONEVERSION option TYPE, which can be constructed from a label in the zone.

The mnemonic for this type is "BACKEND-SERIAL".

The VERSION value for the BACKEND-SERIAL type **MUST** be a copy of the \_version label in the zone.


# Security and Privacy Considerations {#security}

Do a risc assessment if publishing the backend serial is a security issue
before publishing it.

# IANA Considerations {#iana}

This document has no IANA actions


# Acknowledgements

Many thanks to original authors of [@!RFC9660](the ZONEVERSION document).

{backmatter}

