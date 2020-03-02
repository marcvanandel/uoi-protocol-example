# UOI Protocol Example

> **GIVE BUILDINGS A PERSONALITY**
> How can we aggregate and bundle a real-estate object’s distributed data through a **Unique Object Identifier** for all relevant stakeholders, demonstrating the benefits to real-estate developers, home-owners and regulatory bodies?

This quote comes from the [Odyssey Hackathon](https://www.odyssey.org/) challenge [Opening Up Real Estate](https://www.odyssey.org/hackathon-2020-kadaster-fibree-ministry-of-the-interior-challenge-give-buildings-a-personality/):

> Create a new application for dynamic data on buildings and their environment on top of an interoperable, accessible, and ownerless connector. The app should allow for extensive bottom-up adoption of the Unique Object Identifier by all relevant stakeholders.
> 
> Watch the challenge deep dive video: https://youtu.be/oYwXJMTAnRw

In this repo is an example of a slightly different appraoch than currently proposed providing some implementation direction on how an UOI and possibly part of the protocol might work.
The current proposal is the following patterns:

| <span style="color: red;">ISO3166</span> | <span style="color: blue;">TYPE</span> | <span style="color: yellow">UOI</span> |
|------------------------------------------|----------------------------------------|----------------------------------------|
| 2 positions                              | 3 positions                            | 16 positions

**ISO3166** is the standard for Country Code. NL for The Netherlands ;-)

**TYPE** refers to a certain type for this UOI.
This might also be interpreted as a context.
For example: a building.
There are forseen multiple layers of types,
each layer has one or a few TYPE definitions.

The **UOI** part is a String, a text with numbers and characters.
This could be the already existing ID already available in the data, 
for example the BAG_ID.

My proposal for this is using another standard: [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) - ISO/IEC 9834-8:2005.
This is a longer but already existing and used standard of 32 characters (instead of above mentioned 16 positions).
This standard has multiple implementations for generating an Universal Unique ID:

- default: version 1 -> globally unique generated ID
- per type: version 5 -> hash from existing ID with a namespace

With this approach it is possible to generate non-linked and unique UOI parts but also generate a hash for the existing IDs.
This could be a conformation per ID.
For example: BAG.PAND.1234567890123456 > 123e4567-e89b-12d3-a456-426655440000
