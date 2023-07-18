---
v: 3

title: >
  CoRE Target Attributes Registry
abbrev: CoRE Target Attributes Registry
docname: draft-ietf-core-target-attr-latest
# date: 2023-03-01
updates: 9176

keyword: Internet-Draft
cat: info
stream: IETF
wg: CoRE Working group

venue:
  mail: "core@ietf.org"
  github: core-wg/core-target-attr

pi: [toc, sortrefs, symrefs, compact, comments]

author:
  -
    name: Carsten Bormann
    org: Universität Bremen TZI
    street: Postfach 330440
    city: Bremen
    code: D-28359
    country: Germany
    phone: +49-421-218-63921
    email: cabo@tzi.org

contributor:
- name: Jaime Jiménez
  organization: Ericsson
  email: jaime@iki.fi
  contribution: Jaime provided the list of initial registrations.

normative:
  RFC8288: linking
  BCP26:
    -: ianacons
    =: RFC8126
  STD80:
    -: ascii
    =: RFC20

informative:
  RFC6690: link-format
  RFC7252: coap
  RFC7641: obs
  RFC8075: http-proxy
  RFC8613: oscore
  RFC5988: linking-old
  RFC9176: rd

--- abstract

The Constrained RESTful Environments (CoRE) specifications apply Web
technologies to constrained environments.
One important such a technology is Web Linking, which CoRE specifications
use as the basis for a number of discovery protocols, e.g., the
Link Format in CoAP's Resource Discovery Protocol and the Resource Directory (RD).

Web Links can have target attributes, the names of which are not
generally coordinated by the Web Linking specification.
This document introduces an IANA registry for coordinating names of target
attributes when used in CoRE.
It updates the IANA RD Parameters registry to coordinate with
this registry.

--- middle

Introduction        {#intro}
============


The Constrained RESTful Environments (CoRE) specifications apply Web
technologies to constrained environments.
One important such technology is Web Linking {{-linking}}, which CoRE
uses as the basis for a number of discovery protocols, such as the
Link Format {{-link-format}} in CoAP's Resource Discovery Protocol ({{Section 7.2
of -coap}}) and the Resource Directory {{-rd}}.

Web Links can have target attributes.
The original Web Linking specification ({{Section 3 of -linking-old}}) did not attempt
to coordinate names of target attributes except for providing common
target attributes for use in the Link HTTP header.
The current revision of that specification clarifies ({{Section 2.2 of -linking}}):

{:quote}
>    This specification does not attempt to coordinate the name of target
   attributes, their cardinality, or use.  Those creating and
   maintaining serialisations SHOULD coordinate their target attributes
   to avoid conflicts in semantics or syntax and MAY define their own
   registries of target attributes.

This document introduces an IANA registry for coordinating names of target
attributes when used in Constrained RESTful Environments, with
specific instructions for the designated expert for this registry ({{de-instructions}}).
It updates the RD Parameters Registry of {{-rd}} to coordinate with
this registry.

With a registry now available, registration of target attributes is strongly encouraged.
The incentive is that an unregistered attribute name might be registered with a different meaning at any time.


Terminology
-----------

{::boilerplate bcp14-tagged}

IANA Considerations
===================

This specification defines a new Target Attributes sub-registry in
the CoRE Parameters registry {{!IANA.core-parameters}}, with the policy
"Expert Review" ({{Section 4.5 of -ianacons}}).

## Instructions for the Designated Expert {#de-instructions}

The expert is requested to guide the registrant towards reasonably
short target attribute names where the shortness will help conserve
resources in constrained systems, but also to be frugal in the
allocation of very short names, keeping them in reserve for
applications that are likely to enjoy wide use and can make good use
of their shortness.

The expert is also instructed to direct the registrant to provide a
specification ({{Section 4.6 of -ianacons}}), but can make exceptions,
for instance when a specification is not available at the time of
registration but is likely forthcoming.

Any questions or issues that might interest a wider audience might be
raised by the expert on the core-parameters@ietf.org mailing list for
a time-limited discussion.
This might include security considerations, or opportunities for
orchestration, e.g., when different names with similar intent are
being or could be registered.

If the expert becomes aware of target attributes that are deployed and
in use, they may also initiate a registration on their own if
they deem such a registration can avert potential future collisions.


## Structure of Entries

Each entry in the registry must include:

{:vspace}
Attribute Name:
: a lower case ASCII {{-ascii}} string that starts with a letter and can
  contain digits and hyphen-minus characters afterward
  (`[a-z][-a-z0-9]*`).
  (Note that {{-linking}} requires target attribute names to be
  interpreted in a case-insensitive way; the restriction to lower case
  here ensures that they are registered in a predictable form).

Brief description:
: a brief description

Change Controller:
: (see {{Section 2.3 of -ianacons}})

Reference:
: a reference document that provides a description of the target
  attribute, including the semantics for when the target attribute
  appears more than once in a link.

## Initial Entries

Initial entries in this sub-registry are as listed in {{pre-reg}}:

| Attribute Name | Brief description                              | Change Controller | Reference                  |
| href           | reserved (not useful as target attribute name) | IESG              | {{RFC6690}}                  |
| anchor         | reserved (not useful as target attribute name) | IESG              | {{RFC6690}}                  |
| rel            | reserved (not useful as target attribute name) | IESG              | {{RFC6690}}                  |
| rev            | reserved (not useful as target attribute name) | IESG              | {{RFC6690}}                  |
| hreflang       | (Web Linking)                                  | IESG              | {{-linking}}                 |
| media          | (Web Linking)                                  | IESG              | {{-linking}}                 |
| title          | (Web Linking)                                  | IESG              | {{-linking}}                 |
| type           | (Web Linking)                                  | IESG              | {{-linking}}                 |
| rt             | resource type                                  | IESG              | {{Section 3.1 of RFC6690}}   |
| if             | interface description                          | IESG              | {{Section 3.2 of RFC6690}}   |
| sz             | maximum size estimate                          | IESG              | {{Section 3.3 of RFC6690}}   |
| ct             | Content-Format hint                            | IESG              | {{Section 7.2.1 of RFC7252}} |
| obs            | observable resource                            | IESG              | {{Section 6 of RFC7641}}     |
| hct            | HTTP-CoAP URI mapping template                 | IESG              | {{Section 5.5 of RFC8075}}   |
| osc            | hint: resource only accessible using OSCORE    | IESG              | {{Section 9 of RFC8613}}     |
| ep             | Endpoint Name (with rt="core.rd-ep")           | IESG              | {{Section 9.3 of RFC9176}}   |
| d              | Sector (with rt="core.rd-ep")                  | IESG              | {{Section 9.3 of RFC9176}}   |
| base           | Registration Base URI (with rt="core.rd-ep")   | IESG              | {{Section 9.3 of RFC9176}}   |
| et             | Endpoint Type (with rt="core.rd-ep")           | IESG              | {{Section 9.3 of RFC9176}}   |
{: #pre-reg title="Initial Entries in the Target Attributes Registry"}

A number of names are reserved as they are used for parameters in
links other than target attributes.
A further set of target attributes is predefined in {{-linking}} and is
imported into this registry.

{{Section 9.3 of RFC9176}} defines the RD Parameters sub-registry.
The present document updates this registry with a note that all
entries with the "A" flag set MUST also get registered over here.

Security considerations
=======================

The security considerations of {{-linking}} apply, as do those of the
discovery specifications {{-link-format}}, {{-coap}}, and {{-rd}}.

--- back

Acknowledgements
================
{: numbered="no"}

The CoRE WG had been discussing setting up a registry for target
attributes since the final touches were made on {{-link-format}}.
The update of the Web Linking specification to {{-linking}} provided the
formal setting, but it took until {{{Jaime Jiménez}}} provided the set of
initial registrations to generate a first version of this specification.
The current version addresses additional input and working group last
call comments by
{{{Esko Dijk}}},
{{{Marco Tiloca}}},
and
{{{Thomas Fossati}}},
and area director review comments from
{{{Rob Wilton}}}.
