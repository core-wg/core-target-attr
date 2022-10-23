---
v: 3

title: >
  CoRE Target Attribute Registry
abbrev: CoRE Target Attribute Registry
docname: draft-bormann-core-target-attr-latest
date: 2022-10-23

keyword: Internet-Draft
cat: info
stream: IETF
wg: CoRE Working group

venue:
  mail: "core@ietf.org"

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
  STD90:
    -: ascii
    =: RFC20

informative:
  RFC6690: link-format
  RFC7252: coap
  RFC5988: linking-old
  RFC9176: rd

--- abstract

The Constrained RESTful Environments (CoRE) specifications apply Web
technologies to constrained environments.
One important such technology is Web Linking {{-linking}}, which CoRE
uses as the basis for a number of discovery protocols, such as the
Link Format {{-link-format}} in CoAP's Resource Discovery Protocol ({{Section 7
of -coap}}) and the Resource Directory {{-rd}}.

Web Links can have Target Attributes, the names of which are not
generally coordinated by the Web Linking specification ({{Section 2.2 of -linking}}).
This short note introduces an IANA registry for coordinating names of Target
Attributes when used in Constrained RESTful Environments.

--- middle

Introduction        {#intro}
============

(Please see abstract.)

The original Web Linking specification {{Section 3 of -linking-old}} did not attempt
to coordinate names of target attributes except for providing common
target attributes for use in the Link HTTP header.
The current revision of that specification clarifies ({{Section 2.2 of -linking}}):

{:quote}
>    This specification does not attempt to coordinate the name of target
   attributes, their cardinality, or use.  Those creating and
   maintaining serialisations SHOULD coordinate their target attributes
   to avoid conflicts in semantics or syntax and MAY define their own
   registries of target attributes.

This short note introduces an IANA registry for coordinating names of Target
Attributes when used in Constrained RESTful Environments.

Terminology
-----------

{::boilerplate bcp14-tagged}

IANA Considerations
===================

This specification defines a new sub-registry for Target Attributes in
the CoRE Parameters registry {{!IANA.core-parameters}}, with the policy
"expert review" ({{Section 4.5 of -ianacons}}).

The expert is instructed to be frugal in the allocation of very short
target attribute names, keeping them in reverse for applications that
are likely to enjoy wide use and can make good use of their shortness.
The expert is also instructed to direct the registrant to provide a
specification ({{Section 4.6 of -ianacons}}), but can make exceptions,
for instance when a specification is not available at the time of
registration but is likely forthcoming.

Each entry in the registry must include:

{:vspace}
Attribute Name:
: a lower case ASCII {{-ascii}} string that starts with a letter and can
  contain digits and hyphen-minus characters afterwards
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


Initial entries in this sub-registry are as listed in {{pre-reg}}:

| Attribute  Name | Brief description                                                                                          | Change Controller | Reference                                        |
| href            | reserved (not useful as target attribute name)                                                             | IESG              | {{RFC6690}}                                        |
| anchor          | reserved (not useful as target attribute name)                                                             | IESG              | {{RFC6690}}                                        |
| rel             | reserved (not useful as target attribute name)                                                             | IESG              | {{RFC6690}}                                        |
| rev             | reserved (not useful as target attribute name)                                                             | IESG              | {{RFC6690}}                                        |
| hreflang        | (Web Linking)                                                                                              | IESG              | {{-linking}}                                       |
| media           | (Web Linking)                                                                                              | IESG              | {{-linking}}                                       |
| title           | (Web Linking)                                                                                              | IESG              | {{-linking}}                                       |
| type            | (Web Linking)                                                                                              | IESG              | {{-linking}}                                       |
| rt              | resource type                                                                                              | IESG              | {{Section 3.1 of RFC6690}}                         |
| if              | interface description                                                                                      | IESG              | {{Section 3.2 of RFC6690}}                         |
| sz              | maximum size estimate                                                                                      | IESG              | {{Section 3.3 of RFC6690}}                         |
| ct              | Content-Format hint                                                                                        | IESG              | {{Section 7.2.1 of RFC7252}}                       |
| obs             | observable resource                                                                                        | IESG              | {{Section 6 of ?RFC7641}}                          |
| osc             | hint: resource only accessible using OSCORE                                                                | IESG              | {{Section 9 of ?RFC8613}}                          |
| oscore-gid      | Group ID of the OSCORE Group (join resource of the Group Manager)                                          | IESG              | {{Section 3 of ?I-D.tiloca-core-oscore-discovery}} |
| app-gp          | endpoint name of the application group associated to the OSCORE Group (join resource of the Group Manager) | IESG              | {{Section 3 of ?I-D.tiloca-core-oscore-discovery}} |
{: #pre-reg title="Initial Entries in the Target Attributes Registry"}

A number of names are reserved as they are used for parameters in
links other than target attributes, a further set is predefined in
{{-linking}}.


Security considerations
=======================

The security considerations of {{-linking}} apply, as do those of the
discovery specifications {{-link-format}}, {{-coap}}, and {{-rd}}.

--- back

Acknowledgements
================
{: numbered="no"}

TBD
