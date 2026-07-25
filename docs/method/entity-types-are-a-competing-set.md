---
title: Entity types are a competing set
description: "You can't recognize persons without also modeling cities and companies: the same string is all three, and only the contrast disambiguates. A principle from rule-based extraction that decides whether an LLM extraction schema is actually separable."
---

# Entity types are a competing set

If you build a recognizer for one entity type, you have to build the ones that collide with it too. Recognize persons, and you are forced to also model cities, companies, and often addresses, because the same string is frequently all of them, and only the presence of the alternatives lets you decide which one you're looking at. "Washington" is a person, a city, a state, and a company. "Amazon" is a river and a company. German surnames are constantly also place names. Miss the competing types and you can't disambiguate the one you care about.

I learned this building rule-based extraction systems, long before LLMs, and it transfers directly to how I design extraction schemas today. Most people arriving through the LLM door treat an extraction schema as a *list of things I want*: define PERSON, ask the model for persons. But a schema is really a **system of contrasts**: each type is defined as much by what it excludes as by what it includes. If the schema only has PERSON, the model will cheerfully label every city and company as PERSON, and you will never see the error, because there was no competing class for the wrong answer to lose to.

So when I design a data model for LLM extraction, I include types I don't even care about, purely so the ones I *do* care about have something to be disambiguated against. It's a design move almost nobody makes until they've been burned by it.

The practical consequence is a distinction worth naming: a schema that **looks right** versus one that is **actually separable**. A schema that looks right lists the fields a stakeholder asked for. A schema that's separable is built so that each ambiguous surface form has somewhere correct to go, so the model is choosing between real alternatives instead of pattern-matching into the only slot available. Getting that contrast structure right upstream is what decides whether any downstream measurement even means anything.
