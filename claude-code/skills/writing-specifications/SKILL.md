---
name: writing-specifications
description: Explains how to write technical specifications as these are written quite differently from your normal writing style. Use when writing or updating a technical specification.
license: MIT
metadata:
  authors:
    - Jay Daley (https://github.com/JayDaley)
    - Claude (noreply@anthropic.com)
---

# Language and structure
Specifications are written in language that states what each individual component does as a very short normative statement.  The reader combines these statements through a process of mental inference, the spec does not do it for them.

Use normative keywords deliberately (MUST, MUST NOT, SHOULD, SHOULD NOT, MAY, as in RFC 2119/RFC 8174).  Each keyword expresses a requirement level; choose it consciously and reserve MUST for genuine requirements.  A statement without a normative keyword is descriptive, not normative, and should be recognised as such.

The language should be simple and avoid using specialist terms from outside of the spec.  A good model is Simplified Technical English but that should not be strictly followed.

Specifications are highly structured, using headings, lists, tables, and other layout structures to organise the information and present a hierarchy of detail and importance.  A specification should be highly consistent in this, using the same structures for the same concepts and hierarchies, presented in the same way.  This is critical for the reader to understand the specification.

Repetition and dispersal of information related to a single object/concept is to be avoided if at all possible.

In particular, enumerations are to be avoided, including those that spread across multiple sentences and so are not obviously enumerations.  If an enumeration seems necessary then that points to the need for the original source of information that enumeration is drawn from, to be extended to include the information.  For example there might be a table of objects and if another part of the spec needs to enumerate those objects then this should be done by extending that table, not a separate narrative with the enumeration.

Examples are always kept separate from the normative text, never inline in a normative paragraph, and clearly labelled as examples.

# Technical content
A specification addresses a very specific layer of technical detail and it never goes outside of that into any layer above or below.

Recognise a layer violation as any statement that describes *how* a lower layer implements a requirement, or *why* a higher layer wants it.  The specification states only what its own layer requires; it does not justify itself to the layer above nor prescribe the internals of the layer below.

# Contraindications
What a specification does not look like is long narrative passage with examples, cross references and little structure.

# Checklist
Before returning specification text, verify each of the following.  Any failure means the text is not yet specification-quality.

- Each normative statement is short, independent, and testable on its own.
- Normative keywords (MUST/SHOULD/MAY) are used deliberately, and non-normative text carries none.
- The same concepts and hierarchies use the same structures, presented the same way.
- Information about a single object/concept is in one place, not repeated or dispersed.
- There are no narrative enumerations; enumerable information lives in its source structure (e.g. a table) instead.
- Examples are separated from normative text and clearly labelled.
- Every statement stays within the specification's own technical layer.

# Reference
See [before/after example](references/before-after.md) for a narrative paragraph rewritten as structured normative text.
