# Talk with business expert and product

## What's existing yet ? Is it working ? 

Before we have to take time to check on legacy code.  There are various solutions to check :

- Github : https://github.com/
- Gitlab : https://gitlab.com

Use all git features to find what's happen previously in codebase, like **git blame** or **git log**. 

You have also test folder who can give you some clue on the current system behaviour.

**After code, take time to certified that the existing functionality works on production environment.**

## Think collectively

**A developer must be integrated like a Product owner or Business expert.**

### Example mapping

Example mapping is a technique for fleshing out and gaining clarity around the acceptance criteria for a given story.
It is based on the idea that multiple examples of specific cases convey information better than a single bad abstraction of a concept.

Get together people from your team with different perspectives. At a minimum, you should include:
- Product person who’s discussing the backlog item from the perspective of “Have I described the problem I want solved?”
- A developer who’s looking at the backlog item from the perspective of “ Do I have enough info to solve this problem?
- A tester who’s looking at the backlog item from the perspective of “ What happens when?”

Steps :
1. Start by writing the story
2. Write each of the acceptance criteria, or rules that we already know
3. Illustrate it with one or more examples
4. Think and write uncover questions that nobody in the room can answer

Legend :

![](https://static1.smartbear.co/cucumber/media/blog/ghost/map.png)

Examples :

![](https://blog.ippon.fr/content/images/2020/06/example-mapping-practice.png)

### EventStorming
EventStorming is a flexible workshop format for collaborative exploration of complex business domains.

It comes in different flavours, that can be used in different scenarios:

- to assess health of an existing line of business and to discover the most effective areas for improvements;
- to explore the viability of a new startup business model;
- to envision new services, that maximise positive outcomes to every party involved;
- to design clean and maintainable Event-Driven software, to support rapidly evolving businesses.

Steps :
1. Identifying the domain events (facts) that occur in the system (“user account created”, “reservation created” or “money withdrawn”)
2. Analyze what happens between events – does the former event triggers the later? Is there any business logic? If so those events should be separated with a business rule named policy.
3. Find what kind of actions cause the events – is it a user clicking on UI, a call from an external system or ticking clock?
   Those are commands.
4. Mark interactions with external systems
5. Mark an aggregate – a logical group of various commands, events and policies together.

Legend :

![legend](https://passion-to-profession.com/wp-content/uploads/2019/02/Screenshot-2019-02-11-at-17.39.03.png)

Examples :

![example](https://passion-to-profession.com/wp-content/uploads/2019/02/CQ-Shop-all.jpg)
![example](https://baasie.com/wp-content/uploads/2020/07/Book-Software-picture4.jpg)

