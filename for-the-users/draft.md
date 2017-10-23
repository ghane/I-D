---
title: Considering Human Rights in IETF Decisions
docname: draft-nottingham-for-the-users-06
date: 2017
category: bcp

ipr: trust200902
area: General
workgroup:
keyword: end users
keyword: human rights

stand_alone: yes
pi: [toc, tocindent, sortrefs, symrefs, strict, compact, comments, inline]

author:
 -
    ins: M. Nottingham
    name: Mark Nottingham
    organization:
    email: mnot@mnot.net
    uri: https://www.mnot.net/

normative:

informative:
  CODELAW:
    target: http://harvardmagazine.com/2000/01/code-is-law-html
    title: "Code Is Law: On Liberty in Cyberspace"
    author:
      -
        ins: L. Lessig
        name: Lawrence Lessig
        organization: Harvard Magazine
    date: 2000
  UDHR:
    target: http://www.un.org/en/documents/udhr/
    title: The Universal Declaration of Human Rights
    author:
      -
        organization: United Nations General Assembly
    date: 1948


--- abstract

This document mandates that human rights be given the same consideration as technical arguments in
IETF decisions, identifies and encourages the development of documentation to aid the application
of human rights considerations to IETF work, and establishes a Human Rights Review Directorate.


--- note_Note_to_Readers

The issues list for this draft can be found at <https://github.com/mnot/I-D/labels/for-the-users>.

The most recent (often, unpublished) draft is at <https://mnot.github.io/I-D/for-the-users/>.

Recent changes are listed at <https://github.com/mnot/I-D/commits/gh-pages/for-the-users>.

See also the draft's current status in the IETF datatracker, at
<https://datatracker.ietf.org/doc/draft-nottingham-for-the-users/>.

--- middle

# Introduction

The IETF, while focused on technical matters, is not neutral about the purpose of its work in
developing the Internet {{?RFC3935}}:

> The IETF community wants the Internet to succeed because we believe that the existence of the Internet, and its influence on economics, communication, and education, will help us to build a better human society.

and, from the same document:

> The Internet isn't value-neutral, and neither is the IETF. We want the Internet to be useful for communities that share our commitment to openness and fairness. We embrace technical concepts such as decentralized control, edge-user empowerment and sharing of resources, because those concepts resonate with the core values of the IETF community. These concepts have little to do with the technology that's possible, and much to do with the technology that we choose to create.

However, the IETF is most comfortable making what we believe to be purely technical decisions; our
process is defined to favor technical merit, through our well-known bias towards "rough consensus
and running code".

Nevertheless, the running code that results from our process (when things work well) inevitably has
an impact beyond technical considerations, because the underlying decisions afford some uses while
discouraging others; while we believe we are making purely technical decisions, in reality that may
not be possible. Or, in the words of Lawrence Lessig {{CODELAW}}:

> Ours is the age of cyberspace. It, too, has a regulator... This regulator is code — the software and hardware that make cyberspace as it is. This code, or architecture, sets the terms on which life in cyberspace is experienced. It determines how easy it is to protect privacy, or how easy it is to censor speech. It determines whether access to information is general or whether information is zoned. It affects who sees what, or what is monitored. In a host of ways that one cannot begin to see unless one begins to understand the nature of this code, the code of cyberspace regulates.

This impact has become significant. As the Internet increasingly mediates key functions in
societies, it has unavoidably become profoundly political; it has helped people overthrow
governments and revolutionize social orders, control populations and reveal secrets. It has created
wealth for some individuals and companies, while destroying others'.

This begs the question of what criteria are used when making decisions in the IETF; a technical
meritorious proposal can and often does have profound effects -- positive or negative -- on various
parties.

Rather than develop principles internally -- which the IETF has neither the expertise nor the
mandate to do -- it is more suitable to adopt externally-developed principles that are broadly
perceived to be authoritative; namely, the United Nations' Universal Declaration of Human Rights
{{UDHR}}.

To that end, this document:

* Mandates that human rights be given the same consideration as technical arguments in
  {{considering}},
* identifies and encourages the development of further documentation to aid the application of
  human rights considerations to IETF work in {{developing}}, and
* establishes a Human Rights Review Directorate in {{review}}.


# Considering Human Rights in IETF Decisions {#considering}

In IETF decisions, arguments supporting human rights are to be given the same consideration as
technical arguments.

Here, "IETF decisions" include those by Working Groups, Area Directors, the IESG as a whole and the
IAB, and "human rights" are as defined by the United Nations' Universal Declaration of Human Rights
{{UDHR}}.

In doing so, the IETF is acknowledging that human rights considerations are important to our work
product, and that by extension that the UDHR is the recognised authoritative definition of them.

This does not mean that human rights arguments automatically overcome technical considerations;
just as with technical discussions, there are often subtleties to understand and tradeoffs to be
made.

It also does not require those making decisions to actively evaluate every proposal for human
rights considerations; rather, it only requires that arguments motivated by human rights get equal
consideration to technical arguments when they are brought to our attention.


# Developing Human Rights Guidance {#developing}

To help apply the policy in {{considering}} the IETF will, from time to time, publish guidance
outlining how specific human rights are applicable to IETF decisions.

For example, Article 19 can be seen to be supported by existing advice on Privacy Considerations
for Internet Protocols {{?RFC6973}}, along with {{?RFC7258}} (Pervasive Monitoring) and
{{?RFC7754}} (filtering).


# The Human Rights Review Directorate {#review}

To support the policy in {{considering}} and to develop the IETF's ability to align its work
product with human rights, a Human Rights Review Directorate will be established.

It is expected that the directorate's membership will:

* Review IETF documents that have potential impact on Human Rights
* Discuss the resulting issues with specification authors, Working Groups and other parties
* Hold face-to-face meetings at IETF meetings
* Create training material based upon the guidance outlined in {{developing}}, and present it at IETF meetings and elsewhere

Members of the Directorate will be selected and overseen by the IETF Chair.


# IANA Considerations

This document does not require action by IANA.

# Security Considerations

This document does not have direct security impact.


--- back

# Acknowledgements

Thanks to Edward Snowden for his comments regarding the priority of end users at IETF93.

Thanks to Harald Alvestrand for his substantial feedback and Niels ten Oever and Martin Thomson for
their suggestions.

