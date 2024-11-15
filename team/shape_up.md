# 🌿 Shape Up

## Context

In an agile mindset, my team regularly reflects on how to improve our way of working. Currently, it is derived from Scrum but with some accomodations and still some pain points. This post summarizes the Shape Up methodology[^shapeup], in particular with respect to Scrum, before exploring ways we could enrich our workflow.

Thanks to [Glenn F. Henriksen](https://github.com/henriksen) for his great talk on Shape Up[^nobacklog], which I immediately added to my [playlist on agility](https://youtube.com/playlist?list=PLSV9dt-aYRC5dHpkeXhqfEA2wLLF4QQ9l).

[^nobacklog]: Glenn F. Henriksen, "Ditch your Backlog and Shape Up your product development" CPH DevFest 2024. https://youtu.be/czd26hnEiiM

[^shapeup]: Ryan Singer "Shape Up Stop Running in Circles and Ship Work that Matters" https://basecamp.com/shapeup

## Definition

Shape Up gets its name from the shaping process.

> Shaping — the pre-work we do on projects before we consider them ready to schedule.
> [...]
> Projects are defined at the right level of abstraction: concrete enough that the teams know what to do, yet abstract enough that they have room to work out the interesting details themselves.

The basic idea is that during a six-week cycle, the team is either responsible of one such project ("large batch") or a few of such projects ("small batch").

## Comparison with Scrum

Lets compare the main notions of Shape Up with their Scrum counterparts[^scrum].

[^scrum]: Ken Schwaber & Jeff Sutherland, "The Scrum Guide" 2020. https://scrumguides.org/

### Sprint vs Cycle

Sprints and Cycles are quite close as they are the heartbeat of the work being done. The Scrum Guide states that "each Sprint may be considered a short project" which is very close to a "large batch" cycle.

#### Length

Both are of fixed length to create consistency.

A Sprint is one month or less with a preference for the latter. "Shorter Sprints can be employed to generate more learning cycles and limit risk of cost and effort to a smaller time frame."

Shape Up finds that "six weeks is long enough to build something meaningful start-to-finish and short enough that everyone can feel the deadline looming from the start, so they use the time wisely."

#### Completeness

Shape Up uses a 2-week [Cool-down](https://basecamp.com/shapeup/2.2-chapter-08#cool-down) during which "programmers and designers on project teams are free to work on whatever they want. After working hard to ship their six-week projects, they enjoy having time that’s under their control. They use it to fix bugs, explore new ideas, or try out new technical possibilities."

On the other hand, Scrum insists on the back-to-back chaining of Sprints. This could seem to conflict with the [definition of Scrum](https://scrumguides.org/scrum-guide.html#scrum-definition) where the ordering of the backlog (point 1.) and inspection and adjustments (point 3.) seem separate from the sprint execution (point 2.).

Note that Cool-downs are also when the choices for the next cycle are done.

### Backlog item vs Project (Raw idea → Pitch → Bet)

In Scrum, the work is composed of Backlog items (also called "work" in the guide, or "stories" in the community) which are turned into Increments of value by the Team. The guide is not prescriptive into what makes an item "ready for selection".

> Product Backlog items that can be Done by the Scrum Team within one Sprint are deemed ready for selection in a Sprint Planning event. They usually acquire this degree of transparency after refining activities. Product Backlog refinement is the act of breaking down and further defining Product Backlog items into smaller more precise items. This is an ongoing activity to add details, such as a description, order, and size.

Shape Up is much more explicit on the life cycle of a Project before it is ready to enter development (see [Principles of Shaping](https://basecamp.com/shapeup/1.1-chapter-02)):

1. Set boundaries.
2. Rough out the elements.
3. Address risks and rabbit holes.
4. Write the pitch

Shape up provides two distinct words two differentiate an idea to be matured, namely a *raw idea*, and a ready one, namely a *pitch*. The pitch shall be bounded, and rough yet solved. A pitch selected for development is called a *bet* to convey that a payout is expected at the end.

### Sizing vs Appetite (🚧TODO🚧)

### Product Backlog vs Decentralized lists

The Product Backlog contains the Backlog items that remain to be done.

> The Product Backlog is an emergent, ordered list of what is needed to improve the product. It is the single source of work undertaken by the Scrum Team.

We note that though the Scrum Guides limits this backlog to required items, it is a very common practice to have backlogs growing to very large sizes due to deprecated items. Also, as a centralized list, its management is concentrated on the Product Owner: the creation of the items, their ordering.

Shape Up uses a decentralized approach.

> Everyone can still track pitches, bugs, requests, or things they want to do independently without a central backlog. Support can keep a list of requests or issues that come up more often than others. Product tracks ideas they hope to be able to shape in a future cycle. Programmers maintain a list of bugs they’d like to fix when they have some time.

This does not mean that no list exists. But they are not required to be centralized, nor managed with the same tools or processes.

### Sprint Planning vs Betting

Sprint Planning addresses three topics:

1. Why is this Sprint valuable?
2. What can be Done this Sprint?
3. How will the chosen work get done?

Conceptually, it is hard to see how the first point precedes the second one. If items follow the story guidelines of bringing value on their own. Then a natural order for the backlog is by dependencies and by decreasing value, and the second point more or less boils down to how many of the top stories the team can commit to. It comes that the Spring Goal is defined by the value of the stories that are to be done.

Shape Up enforces that each pitch provides value on its own. And as only doable pitches are reviewed (see [Questions to ask](https://basecamp.com/shapeup/2.3-chapter-09#questions-to-ask)), the choice (what will be done) is left to the stakeholders (in Basecamp case, the CEO, CTO, senior dev & product strategist) instead of with the team. Then, there is a [responsibility hand over](https://basecamp.com/shapeup/3.1-chapter-10) to the team who is then responsible of figuring how to do the work.

### Sprint Backlog vs Scope Map

The Sprint Backlog is the continuation of the Product Backlog but for developpers to work on the items selected during Planning.

> The Sprint Backlog is a plan by and for the Developers. It is a highly visible, real-time picture of the work that the Developers plan to accomplish during the Sprint in order to achieve the Sprint Goal. Consequently, the Sprint Backlog is updated throughout the Sprint as more is learned. It should have enough detail that they can inspect their progress in the Daily Scrum. 

Shape Up proposes to track progress via a todo list called [Scope Map](https://basecamp.com/shapeup/3.3-chapter-12#the-scope-map).

> The scopes reflect the meaningful parts of the problem that can be completed independently and in a short period of time—a few days or less. They are bigger than tasks but much smaller than the overall project.

Both methods acknowledge that the work is not completely known in advance.

## Summary: Shape Up ~ Scrum + Shaping + Cooldown

In summary, one could summarize Shape Up as Scrum with a prescriptive refinement process, namely the shaping process.

The main parts where Shape Up goes against the Scrum Guide is:

* The length of Sprints. Cycles are 6 week long
* The Cooldown period between sprints.
* The absence of a Product Backlog.

But in other ways, Shape Up solves the Scrum contradiction on focus. Teams cannot realistically only do work to improve the Product ("[Product Backlog] is the single source of work undertaken by the Scrum Team"). Cooldowns allow for greater focus during the cycle.
 
## Next steps (🚧TODO🚧)