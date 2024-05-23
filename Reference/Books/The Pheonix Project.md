2405211638
	Status: #book 
		Tags: 

# The Pheonix Project


---

Every 500 years, a majestic bird with fire-colored feathers, feeling that death was close, would build a nest high in the tree tops so the sun would burn it down… And then a tiny newborn bird would rise from ashes, growing again, beautiful as ever. 

In many cultures, a phoenix was a symbol of resurrection. The meaning of this symbol has been transformed over years, and now it can be treated as a metaphor of renewal, of good changes happening after a huge failure.  

_The Phoenix Project: A Novel About IT, DevOps, and Helping Your Business Win_ is built on this ancient metaphor. 

This business novel, written by Gene Kim, Kevin Behr, and George Spafford, tells us about the story of “Parts Unlimited”, a fictional company that was going through a serious crisis and was on the verge of collapsing. 

To save the company, the leadership tried to launch a new project – Phoenix – which, they hoped, would close the gap with competition. Analyzing the problems and finding solutions, they managed to make the company profitable and bring it to a new level.    

Containing some core concepts of effective business strategies, “The Phoenix Project” is still a fictional text. Relationships among characters, their discussions and attempts to improve the situation, failures and successes greatly illustrate how exactly the techniques and approaches the authors talk about work in real life. 

As the story unfolds, we see how the company, just like a mythological phoenix, rises from ashes.

## Plot

In a nutshell, the protagonist of the novel, Bill Palmer, an IT director at automotive parts manufacturer and retailer company “Parts Unlimited”, is promoted to Vice President of IT. Steve Masters, the CEO of the company, asks him to “undertake some kamikaze mission” and help the company to regain profitability, increasing their market share and keeping customers.

Bill unwillingly accepts the offer and, together with system manager Wes, and Patty, the director of IT service support, starts fighting numerous issues that begin to snowball: a problem with payroll that puts employees at risk of not getting paid, security breaches that obviously didn’t comply with state regulations, and many others. 

The situation was getting out of control, but at some point, Bill meets a very interesting character – Dr. Erik Reid.      

Erik, a new board member, plays a central role in the novel. As Bill notes, he is like Master Shifu in the “Kung Fu Panda” movie, sharing wisdom and coaching Bill to find answers by himself. 

To explain why the company is failing and what can be done to save it, Erik takes Bill to one of the company’s manufacturing plants. He believes that the principles used in manufacturing are the same as those needed at IT, so he physically shows Bill how the system works. Just like manufacturing needs maintenance policies, IT needs preventive measures, otherwise the business may suffer:

> _People think that just because IT doesn’t use motor oil and carry physical packages that it doesn’t need preventive maintenance… That somehow, because the work and the cargo that IT carries are invisible, you just need to sprinkle more magic dust on the computers to get them running again... showing how IT risks jeopardize business performance measures, you can start making better business decisions._

Step by step, Bill understands the connection and applies the principles, admitting that he has no idea how companies who don’t use them survive.

In our “Phoenix Project” summary, we will not retell the fictional part of the novel: we will focus on the most important concepts Bill discovered and applied.

## Concept 1. The Three Ways

One of the most important concepts Erik tells Bill about is “the Three Ways” – the main principles on which DevOps are built. The Three Ways are about providing value to the customers by creating a culture where employees cohesively work together, understanding  the interrelations between different parts of one business system. As Erik says to Bill, 

> _Your job as VP of IT Operations is to ensure the fast, predictable, and uninterrupted flow of planned work that delivers value to the business while minimizing the impact and disruption of unplanned work, so you can provide stable, predictable, and secure IT service._

So what are the Three Ways Erik is talking about?

### The First Way

The First Way concerns the processes between the business and the customer – in particular, it explains how to create a fast flow of work from Development into IT operations, and then to the customer.

According to this principle, to maximize the flow, you need to optimize for global goals. So, instead of focusing on local goals like Ops availability measures, you’d need to have a bigger picture in mind which you’d strive for. The entire system is more important than specific departments.

The authors provide the following measures to create the fast flow:

- Building systems and organizations that are safe to change;
- Limiting work in process;
- Continuous integration and deployment;
- Creating environments on demand.

In the book, the First Way – creating flow – took place when Bill tried to organize the change process, making his people put their intended changes on index cards and then put the cards on a kanban board. The cards visualized the work in progress in a way that everyone could see.

It’s important to mention here that the kanban board, as Patty explains, is “one of the primary ways our manufacturing plants schedule and pull work through the system” - this is one of the proofs of similarity between IT and manufacturing.

To limit the work in process (WIP), she makes a decision to visually demonstrate all the activities involving their key resources on the kanban board, where index cards will be arranged in four rows: “Move worker office,” “Add/change/delete account,” “Provision new desktop/laptop,” and “Reset password”, diving each of the rows into three columns labeled “Ready”, “Doing”, and “Done.”

She insists that all important activities must go through the board, not by emails, phone calls, or messaging: if it’s not on there, it won’t be done, and if it is on there, it will be done faster:

> _You’d be amazed at how fast work is getting completed, because we’re limiting the work in process. Based on our experiments so far, I think we’re going to be able to predict lead times for work and get faster throughput than ever._

In addition to that, an important part of the First Way which the company was missing was the disability to distinguish what work mattered versus what did not. As Erik pointed out, taking needless work out of the system is more important than putting more work into it.

This is why it is mandatory to know what exactly can help achieve business objectives – projects, security, compliance with regulations etc. After all, it is the outcomes that really matter, not the work you do.

### The Second Way

The Second Way is about fixing quality at the source in order to avoid rework. This is possible due to constant flow of fast feedback that helps not make the same mistakes and enable faster detection and recovery of problems. “A feedback loop” should go from the earliest parts of product definition, design, and development. This way, the quality is created at the source.

The practices necessary to apply the Second Way are:

- Stopping “the production line” when builds and tests fail in the deployment pipeline;
- Constantly improve daily work
- Create a better cooperation between Development and IT Operations – “shared goals and shared pain”;
- Create production telemetry to make sure code and environments work properly and that customers requirements are satisfied.

A critical part of the Second Way, as Erik explains, is making wait times visible – which is, knowing when your work has to wait to be done (since the resource who is supposed to do it is busy) or when your work has to go back through the process (because it needs to be redone or lacks some parts). 

The wait time is “the percentage that resource is busy, divided by the percentage that resource is idle” – for example, if the resource is fifty percent utilized, the wait time is 50/50, which means that you have to wait for 50 percent of his time to get your work processed.

Erik gives an example: at his plant, specific components were never showing up on an assembly line, but it was not because they didn’t have resources or tasks were taking too long; following the parts around, they found out that the parts were in queues.

He insists that the same happens at Bill’s “plant”: people believe that their personal project is a top priority, and want it to be finished first, at the expense of everything else.

To help Bill understand where the root of the evil is, Erik asks him: do the projects people are pushing increase operational stability? Do they decrease the time required to detect and recover from security breaches? Do they increase the capacity of the most constrained resource of the company, Brent? The answer is obvious – those projects are not a good use of time.  

The need for amplification of feedback loops is another important part of the Second Way. A huge problem the company was struggling with was the low data quality, which made it impossible to do any sort of forecasting:

> _Most of the time, we’re flying blind… The best data that we have right now comes from interviewing our store managers every two months and the customer focus groups we do twice a year. You can’t run a billion-dollar business this way and expect to succeed!_

Evidently, what they needed to do was to start collecting accurate and timely information from their stores and online channels to create appropriate marketing campaigns and provide the right products – that was the only way to increase their market share.  

### The Third Way

The final way shows how to create a culture that “fosters experimentation, learning from failure, and understanding that repetition and practice are the prerequisites to mastery.”

The practices necessary to create such a culture are as follows:

- Be open to innovation and risk taking instead of blindly taking orders;
- High trust;
- Allocating at least 20 percent of Development and IT operations cycles toward non-functional requirements;
- Encouraging and celebrating improvements.

According to the authors, experimentation requires taking risks and the ability to learn from past mistakes and success. This, in turn, requires courage to do things differently from what you are used to. Even though it may seem scary, it’s a good way to improve the system of work.

As for repetition and daily practice, this helps develop skills and habits that make the work process safe and enable resume normal operations. Erik explains to Bill that a genuine culture of improvement is impossible without practice and drills, emphasizing that five minutes daily is more useful than three hours once a week.

> _The Third Way is all about ensuring that we’re continually putting tension into the system, so that we’re continually reinforcing habits and improving something. Resilience engineering tells us that we should routinely inject faults into the system, doing them frequently, to make them less painful._

Repetition is especially important for teamwork since it creates transparency and, as a consequence, trust. And without trust, any complex business problems cannot be fixed. 

This is why, in one of the chapters, Steve holds a meeting where he tells his people about [“The Five Dysfunctions of a Team”](https://www.runn.io/blog/5-dysfunctions-of-a-team-summary) by Patrick Lencioni – a book about team dynamics which emphasizes the importance of mutual trust and vulnerability at a workplace. Steve suggests using the technique described in the book, telling sensitive information about his private life and encouraging the others to do the same.

Speaking about teamwork, we can also mention that Bill, an ex-soldier who used to serve at the Marine unit, often draws parallels between management in the army and at the company, hoping that his previous experience would help him at his new position. However, Erik explains that the company environment is not like army:

> _What worked for you in the Marines will never work here, considering how they run this circus. Instead of one general in your chain of command, you’ve got ten generals calling the shots here, and all of them have a direct line to each and every private in your company._

The problem, as Erik explains, is that rigor and discipline are not everything: efficiency and processes are not enough to achieve results. He tells Bill that the reason why they fail is that they don’t understand what work actually is – and that there are more than one type of work.

## Concept 2. The Four Types of Work

So, according to Erik, the work IT does can be divided into 4 types:

Business projects. These include business initiatives; they are usually tracked by the [Project Management Office](https://www.runn.io/blog/what-is-a-project-management-office-pmo).

Internal IT projects. This type includes internally generated improvement or Operation projects created by business projects. They are usually tracked not centrally but by individual budget owners (e.g. database or storage managers). 

Changes. Changes – version updates and any other improvements – are often generated by business and internal projects. They are tracked in the ticketing system.

The IT department of “Parts Unlimited” was supporting over 35 business projects through Project Management Office plus more than 70 smaller ones and internal initiatives. These projects created 437 changes which made Bill think these should be treated as a different type of work: these changes were literally defining the work schedule. The changes were smaller than the projects but they still require resources and need to be deconflicted.  

Realizing that serious problems like payroll failure and SAN incident happened because people were not talking to each other about changes they were planning or implementing, Bill made a conclusion they needed a sustainable process of change control that would prevent “friendly-fire incidents”. 

So, he organized a meeting in which he started a new policy - continuously authorizing and scheduling changes, providing the following information: who is the person planning the change; what is the system being changed; and a summary of the change.

However, an interesting issue popped up: it was not clear what can be treated as a “change”. After arguing for half an hour, they reached a consensus on the definition:

> _A ‘change’ is any activity that is physical, logical, or virtual to applications, databases, operating systems, networks, or hardware that could impact services being delivered._

To avoid confusion, the final decision was to submit requests for changes, schedule time for the changes to be reviewed, and get them approved before implementation.

Unplanned work (recovery work). These are operational problems caused by other types of work being done at the expense of work which has actually been planned. 

Unplanned work is not free – after all, it consumes time that could be used otherwise. It leads to chaos, shortcuts, and, as a consequence, more fragile applications (which, due to the domino effect, will create more unplanned work). This is why it needs to be controlled, just like changes.

A great way to decrease the unplanned work is to analyze the capacity initially, before accepting work.  

> _When you spend all your time firefighting, there’s little time or energy left for planning. When all you do is react, there’s not enough time to do the hard mental work of figuring out whether you can accept new work._

One of the biggest problems negatively impacting the Phoenix project was the amount of unplanned work assigned to Brent – the IT genius who supported many people at the same time, fixing their problems. People at the company were constantly bothering Brent, asking him to fix a million things. This distracted him from his main responsibility – Phoenix.

To prevent unplanned work from hitting Brent, they found a solution: to create a resource pool to handle escalations, which would be the only group allowed to access Brent – and only after an official approval. 

This group would have to document all they learned from Brent (because he would never explain how exactly he fixed problems, which made him an irreplaceable asset). Finally, Brent would never be allowed to work on the same problem twice.

This approach would hit two birds with one stone: Brent would focus only on the most important thing, and his colleagues would learn from him.  

## Concept 3. The Theory of Constraints

In one of the conversations with Bill, Erik gives him some home reading – “The Goal” by Dr. Eli Goldratt, which describes the Theory of Constraints. Erik explains that in most plants, there is a small amount of resources (men, machines, or materials) that dictate the outputs of the entire system. 

This amount of resources is called constraint – or bottleneck, and it has an important role in the system work:

“Until you create a trusted system to manage the flow of work to the constraint, the constraint is constantly wasted, which means that the constraint is likely being drastically underutilized.”  

According to Dr. Goldart, there are 5 steps in the Theory of Constraints:

1. Identify the constraint
2. Exploit the constraint
3. Subordinate other activities to constraint
4. Elevate the constraint to new levels
5. Find the next constraint

Applying the Theory of Constraints step by step, you identify the bottleneck and improve the flow of work, since the actions taken without taking the bottlenecks into account bring only short-term results.

As Erik explained, any improvements made besides the bottleneck are illusory: the improvements made after the bottleneck are useless as they still wait for work from the bottleneck, and the improvements made before it result in more problems piling up. 

In “Parts Unlimited”, the person who was the main constraint was Brent. Doing a lot of unplanned work, he constrained many important flows of work, including restoring service. 

As Erik explains, “exploiting the constraint” meant not allowing Brent waste any time: not making him wait for anything, and not letting him focus on anything but his main priority. As a result, the needed application support was outsourced, and Brent was moved outside of the organization.

As we can see from “The Phoenix Project”, conflicts between IT Operations and Development can be resolved with the right approach. Adopting specific cultural norms and implementing effective practices into daily work routine, it is possible to produce a high quality product and satisfy customer requirements. 

Stability and reliability can be preserved even deploying hundreds of changes every day, and high-performing organizations like Amazon, Netflix, and Google prove it. 

Collaborative work, shared goals, experimentation, and a culture of learning are effective means to build quality and functionality, and make the company achieve success in the market.  


---
# Reference