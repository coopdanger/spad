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

This specification defines a simple JSON format and well known URL for
firewalls and other devices to discover whats IP addresses, ports, and
related transports a given cloud services uses.

{mainmatter}

# Introduction

{{spec/overview.md}}

# Terminology

In this document, the key words "MUST", "MUST NOT", "SHOULD", "SHOULD
NOT", "MAY", and "OPTIONAL" are to be interpreted as described in RFC
2119 [@!RFC2119] and indicate requirement levels for compliant
implementations.

RAML is defined at <https://github.com/raml-org>.

JSON Schema is defined at <http://json-schema.org/>. Further
information is available in [@I-D.wright-json-schema].

# Example

To figure out what IP addresses are used by the service example.com,
the first step is to form the query URL by constructing an endpoint at
".well-known/spad/v0/spad".

Then an HTTPS GET query is done that to that URL.

~~~
curl https://example.com/.well-known/spad/v0/spad
~~~

The responses would be a JSON result that could look like

{{gen/example1.json.md}}

The example above indicates that the "example.com" application has a
single service with a single flow that uses only the HTTPS to connect to
port 443 on the IP address "203.0.113.2".  This SPAD information is
not valid after "Fri 11 Nov 2016 22:20:08 UTC" and a new SPAD file
should be retrieved before that point in time.

The following shows a more complex example result for an application
that uses two flows. One is TLS to the SIP port of a server with a v4
and v6 address. The TLS connection will have a name of example.com in
the SNI.  The other flow is media sent over UDP to port 5004 on a few
different ip addresses. If devices in the network are capable of
remarking DSCP, the desired marking is "AF41".


{{gen/example2.json.md}}


# Blueprint

{{spec/blueprint.md}}


# Schemas

{{spec/schemas.md}}


# IANA Consideration

{{spec/iana.md}}

# Security Considerations

{{spec/security.md}}

# Acknowledgements

Thank you for the contributions from:
{{gen/Contributors.md}}


{backmatter}

{{spec/CONTRIBUTING.md}}
