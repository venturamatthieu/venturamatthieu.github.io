# Live your documentation

Do we really need this documentation?
Do we really need this documentation now?
Could we just share knowledge through conversations or working together?

## External vs Internal 

External :
- Feature files used for business-readable specifications and testing tools 
- Markdown files and images next to the code with a naming convention or linked to from the code or feature files 
- Tools manifests, including the dependency management manifest, automated deployment manifest, infrastructure description manifest, and so on

Internal : 
- Self-documenting code and use of clean code practices, including class and method naming, using composed methods and types 
- Annotations that add knowledge to elements of the programming language 
- Javadoc comments on public interfaces, classes, and main methods 
- Folder organization and decomposition and naming of modules and submodules

Prefer internal and remember :

**The best place to put documentation about a thing is on the thing itself.**

## Pimp your code with tag or attribute 

Tag 

```java 
@BoundedContext(name = "Cat Activity")
package com.acme.lolcat.domain

@CoreConcept
interface CatActivity

```

Attributes 
``` java 
public class Foo
{
    [KeyLandmark("The main steps of enriching the Customer Purchase from 
    the initial order to a ready-to-confirm purchase")]
    public void Enrich(CustomerPurchase cp)
    {
        //... interesting stuff here
    }
}

```

Example of tags : 
@wip, @pending, @controversial
@acceptancecriteria @specs @returnpolicy @nominalcase @keyexample
@Documented, @ValueObject @CoreConcept, @DomainService, @DomainEvent, @BusinessPolicy,
@AbstractFactory, @Adapter, @BoundedContext...

## Facilitate business and tech communication

### Easy onboarding 

For tech, you can use a tag @Examplar("comment")

- On a class: @Exemplar("A very good example of a REST resource with content negotiation and the use of URI-templates")
- On a JavaScript file: @Exemplar("The best example of integrating Angular and Web Components")
- On a package or a key class of this part of design: @Exemplar("A nicely designed example of CQRS")
- On a particular class: @Exemplar(pros = "Excellent naming of the code", cons = "too much mutable state, we recommend immutable state")

You can do more, like in tourism industry, organize a visit of your code.

Sightseeing Map (max 10 places) :
- KeyLandmark or Landmark
- MustSee
- CoreConcept or CoreProcess
- SightSeeingSite
- PlaceOfInterest, PointOfInterest, or POI
- TopAttraction
- KeyAlgorithm or KeyCalculation


### Living Glossary
Generate an output who contains all important concept. It's based on a defined tag, like @glossary.

### Living Diagram
Generate diagrams from different sources : 
- story
- architecture design (package name, extend, interface)

## Exhausted Tools list 
- Doclet 
- AsciiDoc 
- picklesdoc 
- Specflow 
- Relish 
