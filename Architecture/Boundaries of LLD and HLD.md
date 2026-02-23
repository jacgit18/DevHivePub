---
tags: 
author:
  - gitUserNamePlaceHolder
banner: "![[Banner.gif]]"
banner_x: 
banner_y: 
cssclasses:
  - dashboard
Comments: Placeholder comment any thing else you want to mention about the document.
Purpose: This documentation discusses
Status: 
Started: 
EditDate: 
Relates:
---
Short answer: **no — choosing libraries is _not_ inherently low-level design.**  
If you treat it that way, you’re collapsing an important distinction and blinding yourself to real architectural decisions.

Now let’s make the boundary precise.

---

## The mistaken assumption you’re making

You’re equating **“code-level artifacts”** with **low-level design**.

That’s a common but shallow shortcut.

Design level is determined by **scope of impact and reversibility**, not by whether it appears in code.

---

## A clean definition (use this)

- **High-level design (HLD):** decisions that shape the _structure, boundaries, and failure modes_ of the system.
    
- **Low-level design (LLD):** decisions that shape _local implementation details_ within those boundaries.
    

Nothing about “libraries” automatically puts them in one bucket.

---

## Where library choices actually land (by type)

### 1. **Foundational libraries**

Examples:

- ORM (Hibernate, Prisma)
    
- Messaging client (Kafka client)
    
- HTTP stack
    
- Auth library
    

**This is high-level design. Period.**

Why:

- They dictate data access patterns
    
- They shape transaction boundaries
    
- They influence performance and consistency
    
- They are expensive to replace
    

Calling this low-level is simply wrong.

---

### 2. **Cross-cutting libraries**

Examples:

- Logging
    
- Observability
    
- Validation
    
- Retry / circuit breakers
    

**This sits in the middle layer** (often called _detailed architecture_).

They:

- Affect every module
    
- Shape operability and failure behavior
    
- Create systemic coupling
    

Not low-level. Not purely high-level either.

---

### 3. **Local utility libraries**

Examples:

- date-fns
    
- lodash
    
- small parsing helpers
    

**This is low-level design.**

Why:

- Local scope
    
- Easy to swap
    
- No architectural gravity
    

This is where the “library = low-level” intuition _sometimes_ comes from — but it doesn’t generalize.

---

## The correct discriminator (memorize this)

Ask:

> **If I change this library, how much of the system breaks?**

|Blast radius|Design level|
|---|---|
|Whole system / data model|High-level|
|Many modules|Mid-level|
|One function|Low-level|

That’s the only rule that consistently works.

---

## Another strong test: _Who cares?_

- Architects care → high-level
    
- Team leads care → mid-level
    
- Individual devs care → low-level
    

If replacing a library requires:

- Migration plans
    
- Data rewrites
    
- Operational changes
    

…it was never low-level design.

---

## Why this distinction matters

Teams routinely under-document:

- ORM choices
    
- Serialization formats
    
- Auth mechanisms
    

Because they label them “implementation details.”

Then six months later:

- The system is boxed in
    
- “Technical debt” magically appears
    
- Everyone pretends it was inevitable
    

It wasn’t. It was misclassified.

---

## Final compression

- **Libraries ≠ low-level by default**
    
- **Foundational libraries = high-level design**
    
- **Utility libraries = low-level design**
    
- **Impact radius > code proximity**
    

If you want, name a few concrete libraries from a real system and I’ll classify each one — and tell you which ones deserve architectural documentation and which don’t.