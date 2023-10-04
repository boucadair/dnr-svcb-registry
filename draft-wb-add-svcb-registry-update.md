---
title: "An Update to the DNS Service Bindings (SVCB) Registry"
abbrev: "DNR & SVCB Registry"
category: info
updates: 9460

docname: draft-wb-add-svcb-registry-update-latest
submissiontype: IETF
number:
date:
consensus: true
v: 3
workgroup: "Adaptive DNS Discovery"
keyword:
 - DNR
 - Service Parameters
 - svcparams


author:
 -
    fullname: Dan Wing
    organization: Cloud Software Group, Inc.
    abbrev: Cloud Software Group
    country: United States of America
    email: [danwing@gmail.com]

 -
    fullname: Mohamed Boucadair
    organization: Orange
    street: Rennes
    code: 35000
    country: France
    email: mohamed.boucadair@orange.com

normative:


informative:
  IANA-SVCB:
    title: DNS Service Bindings (SVCB); Service Parameter Keys (SvcParamKeys)
    target: https://www.iana.org/assignments/dns-svcb/dns-svcb.xhtml
    date: 2023-06-13

--- abstract

This document updates the DNS Service Bindings (SVCB) IANA registry to maintain the set of service parameters that are applicable to Discovery of Network-designated Resolvers (DNR). The document also includes guidance for new service parameters to indicate whether they are eligible to be conveyed in DNR.

This document updates RFC 9460.

--- middle

# Introduction

{{!I-D.ietf-dnsop-svcb-https}} established an IANA registry for Service Parameter Keys (SvcParamKeys) {{IANA-SVCB}}. That registry is leveraged by the Discovery of Network-designated Resolvers (DNR) {{!I-D.ietf-add-dnr}}. However, not all service parameters defined in that registry are eligible for inclusion in DNR. For example, {{!I-D.ietf-add-dnr}} specifies that "ipv4hint" or "ipv6hint" Service Parameters (SvcParams) must not be included in DNR because these parameters are superseded by the other DNR parameters.

Given that future SvcParams may be defined in the future, there is currently no mechanism to tag whether an SvcParam may or must not be included in DNR. This document fixes that issue by updating the structure of the Service Parameter Keys (SvcParamKeys) registry of the DNS Service Bindings (SVCB) registry group {{IANA-SVCB}} to maintain the set of service parameters that are applicable to DNR.

# Conventions and Definitions

{::boilerplate bcp14-tagged}

# Update to Section 14.3.1 of RFC 9460

This document updates {{Section 14.3.1 of !I-D.ietf-dnsop-svcb-https}} as follows:

OLD:
: A registration MUST include the following fields:
  : Number: wire format numeric identifier (range 0-65535)
  : Name: unique presentation name
  : Meaning: a short description
  : Format Reference: pointer to specification text
  : Change Controller: Person or entity, with contact information if appropriate.

NEW:
: A registration MUST include the following fields:
  : Number: wire format numeric identifier (range 0-65535)
  : Name: unique presentation name
  : Meaning: a short description
  : Applicable to DNR: Y/N.
  : Format Reference: pointer to specification text
  : Change Controller: Person or entity, with contact information if appropriate.

# Security Considerations

This document does not introduce new security considerations other than those discussed in {{Section 7 of !I-D.ietf-add-dnr}} and {{Section 12 of !I-D.ietf-dnsop-svcb-https}}.

# IANA Considerations

This document request IANA to update the Service Parameter Keys (SvcParamKeys) registry of the DNS Service Bindings (SVCB) registry group {{IANA-SVCB}} as follows:

* Add a new column entitled "Applicable to DNR (Y/N)". The new column must be added right after the "Meaning" column.
* Set "Applicable to DNR" to "Y" for "alpn", "port", and "dohpath". Set "Applicable to DNR" to "N" for the other remaining entries.
* Update the reference of the registry to list the RFC:

OLD: [RFC-ietf-dnsop-svcb-https-12]
NEW: [RFC-ietf-dnsop-svcb-https-12][This_Document]

--- back

# Acknowledgments
{:numbered="false"}

TBC.
