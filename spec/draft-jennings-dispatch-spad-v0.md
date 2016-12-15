%%%
    title = "Simple Port and Address Discovery"
    abbrev = "SPAD "
    category = "std"
    docName = "draft-jennings-dispatch-spad-v0-latest"
    ipr = "trust200902"
    area = "ART"

    [pi]
    symrefs = "yes"
    sortrefs = "yes"
    toc = "yes"

    [[author]]
    initials = "C."
    surname = "Jennings"
    fullname = "Cullen Jennings"
    organization = "Cisco"
      [author.address]
      email = "fluffy@iii.ca"


%%%

.# Abstract

This specification defines a simple JSON format and well-known URL for
firewalls and other devices to discover what IP addresses, ports, and
related transports a given cloud service uses.

{mainmatter}


# Introduction

Simple Port and Address Discovery (SPAD) allows a web application to
inform others of what ports and IP addresses it uses so that things
like firewalls can correctly re-configure themselves as the ports and
addresses change. Applications are identified by a domain name which
is used to form a URL in a well-known location where a client can do an
HTTPS REST call to get a JSON file that describes information about
what addresses and transports the service uses.


# Terminology

In this document, the key words "MUST", "MUST NOT", "SHOULD", "SHOULD
NOT", "MAY", and "OPTIONAL" are to be interpreted as described in RFC
2119 [@!RFC2119] and indicate requirement levels for compliant
implementations.

RAML is defined at <https://github.com/raml-org>.

JSON Schema is defined at <http://json-schema.org/>. Further
information is available in [@I-D.wright-json-schema].


# Examples

{{spec/examples.md}}


# RAML

The RAML specification for the API is:

{{gen/spad.raml.md}}


# Schemas

The JSON returned in a response MUST correspond to the following JSON schema:

{{gen/spad-schema.json.md}}


# IANA Considerations

TODO - register well known URL usage


# Security Considerations

TODO - explain importance of HTTPS

Discuss merging with existing ACL


# Acknowledgements

TODO - add acknowledgments


{backmatter}

{{spec/CONTRIBUTING.md}}
