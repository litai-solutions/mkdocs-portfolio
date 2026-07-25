---
title: Entity types are a competing set
description: "Why an extraction schema needs the types you do not care about. A fund's excluded sectors, a ruled-out diagnosis: with no competing class, the wrong label has nowhere to go and no metric shows the error."
---

# Entity types are a competing set

If you build a recognizer for one entity type, you have to build the ones that collide with it too. Recognize persons, and you are forced to also model cities, companies, and often addresses, because the same string is frequently all of them, and only the presence of the alternatives lets you decide which one you're looking at. "Washington" is a person, a city, a state, and a company. "Amazon" is a river and a company. German surnames are often place names as well. Miss the competing types and you can't disambiguate the one you care about.

I learned this building rule-based extraction systems, long before LLMs. That surface problem is now easy: ask a current model whether "Washington" is a person or a city and it answers from context, with no help from the schema. But the principle survives where the collision is a matter of judgment.

A venture fund's investment policy is a good case. *"We invest in early-stage climate hardware."* *"We do not invest in tobacco, gambling, or defense."* *"We did consumer until 2023 and stopped."* All three sentences name sectors, and a schema with a single `sectors_of_interest` field has one slot for all of them. The model puts tobacco in it, because tobacco appeared in an investment-policy sentence and there was no `excluded_sectors` class for it to go to. You now have a fund that reads as investing in tobacco, and no metric will show it, because the only label the schema allowed is the label it got.

Clinical text has the same shape. The same condition name arrives as an active diagnosis, as family history, as a risk factor, and as something explicitly ruled out. A schema with only `diagnosis` collapses four different clinical facts into one, and *"mother has diabetes"* becomes a patient with diabetes.

So when I design a data model for LLM extraction, I include types I don't even care about, purely so the ones I *do* care about have something to be disambiguated against.

The practical consequence is a property worth naming: **separability**. A separable schema is built so that each ambiguous surface form has somewhere correct to go, which leaves the model choosing between real alternatives. A schema that lists only the fields a stakeholder asked for gives it one slot to pattern-match into, and the measurement downstream inherits that flaw: every metric is computed over labels the schema made unfalsifiable.
