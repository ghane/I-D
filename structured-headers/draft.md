---
title: 
abbrev: 
docname: draft-nottingham-structured-headers-00
date: 2015
category: info

ipr: trust200902
area: General
workgroup: 
keyword: Internet-Draft

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
  RFC2119:

informative:


--- abstract


--- note_Note_to_Readers

*RFC EDITOR: please remove this section before publication*

The issues list for this draft can be found at <https://github.com/mnot/I-D/labels/structured-headers>.

The most recent (often, unpublished) draft is at <https://mnot.github.io/I-D/structured-headers/>.

Recent changes are listed at <https://github.com/mnot/I-D/commits/gh-pages/structured-headers>.

See also the draft's current status in the IETF datatracker, at
<https://datatracker.ietf.org/doc/draft-nottingham-structured-headers/>.


--- middle

# Introduction

Specifying new HTTP headers is an onerous task; even with the guidance in {{?RFC7231}}, Section 8.3.1, there are many decisions -- and pitfalls -- for a prospective HTTP header author.

Likewise, writing parsers for HTTP headers is often painful, because each header has slightly different handling of what looks like common syntax. 

This document introduces "structured headers" to HTTP to address these problems. Structured headers define a generic abstract model for data, along with a concrete syntax for expressing that model in textual HTTP headers.

In doing so, it allows new headers to be defined much more easily and reliably, using the guidance in {{defining}}. Likewise, it offers a single parsing model for the headers that use the syntax, as defined in {{parsing}}.

Additionally, future versions of HTTP can define alternative serialisations of the abstract model, allowing headers that use it to be transmitted more efficiently without being redefined.

Note that it is not a goal of this document to redefine the syntax of existing HTTP headers; the mechanisms described herein are only intended to be used with headers that explicitly opt into them.
 

## Notational Conventions

The key words "MUST", "MUST NOT", "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT",
"RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as
described in BCP 14 {{!RFC2119}} {{!RFC8174}} when, and only when, they appear in all capitals, as
shown here.

# Structured Header Values

A structured header value is a HTTP header field-value {{RFC7230}} that uses the conventions defined in this document.

{{types}} defines a number of data types that can be used in structured headers, but only three are allowed at the "top" level; lists, dictionaries, or items.

To help parsers identify a structured header value, its first non-whitespace character MUST be a sigil.


FooHeader: [ list ]
BarHeader: { dictionary }
BazHeader: > item


# Structured Header Value Types {#types}

Structured headers can incorporate the following value types:

## Numbers

Abstractly, numbers in structured headers are integers within the range -(2**53)+1 to (2**53)-1, with an optional fraction component. They MUST NOT include numbers that express greater magnitude or precision than an IEEE 754 double precision number ({{IEEE754}}) provides.

The textual HTTP serialisation of numbers is compatible with JSON numbers, although it does not include exponents.

~~~
number        = [ "-" ] int [ frac ]
int           = zero / ( digit1-9 *14DIGIT )
frac          = "." 1*10DIGIT
digit1-9      = %x31-39   ; 1-9
~~~

Structured header parsers that encounter numbers outside the range -(2**53)+1 to (2**53)-1 MUST consider the value to be in error.


## Strings

Abstractly, strings in structured headers are Unicode strings {{UNICODE}} that MUST NOT include code points that identify Surrogates or Noncharacters as defined by [UNICODE].

The textual HTTP serialisation of strings uses percent-encoding {{RFC3986}} for all non-ASCII characters, as well as double quotes.

~~~
string = DQUOT *char DQUOT
char = unescaped /
  escape (
      %x22 /          ; "    quotation mark  U+0022
      %x5C /          ; \    reverse solidus U+005C
      %x2F /          ; /    solidus         U+002F
      %x62 /          ; b    backspace       U+0008
      %x66 /          ; f    form feed       U+000C
      %x6E /          ; n    line feed       U+000A
      %x72 /          ; r    carriage return U+000D
      %x74 /          ; t    tab             U+0009
      %x75 4HEXDIG )  ; uXXXX                U+XXXX
escape = %x5C              ; \
unescaped = %x20-21 / %x23-5B / %x5D-10FFFF
~~~

## Label

Labels are short identifiers; their abstract syntax is identical to their expression in the textual HTTP serialisation. 

~~~
label = ALPHA *( ALPHA / DIGIT / _ / - )
~~~

## Binary

Arbitrary binary content can be conveyed in structured headers. In the textual serialisation, they are indicated by a leading "*", with the data encoded using BASE64.

~~~
binary = '*' 1*base64
~~~

MUST NOT pad

## item

An item is can be a number, string, label or binary content.

~~~
item = number / string / label / binary
~~~

## Dictionary

Dictionaries are arbitrary-length arrays of key-value pairs, where the keys are labels and the values are items. Keys are required to be unique.

In the textual HTTP serialisation, keys and values are separated by "=" (without whitespace), and key/value pairs are separated by a comma with optional whitespace.

~~~
dictionary = label "=" item *( OWS "," OWS label "=" item )
~~~


## List

Lists are arbitrary-length arrays of items. In the textual HTTP serialisation, each item is separated by a comma and optional whitespace.

~~~
list = item *( OWS "," OWS item )
~~~


# Parsing Structured Headers

Note that empty headers are not allowed by the syntax, and must be considered errors.

# Specifying Structured Headers


versioning

# Security Considerations


--- back
