# Agile Development

## Table of Contents
1. [Agile Manifesto](#agile-manifesto)
1. [Sprint Planning](#sprint-planning)
1. [Standup](#standup)
1. [Pairing & Mobbing](#pairing-&-mobbing)
1. [Code Review](#code-review)

## Agile Manifesto
1. Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.
1. Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage.
1. Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
1. Business people and developers must work together daily throughout the project.
1. Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
1. The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
1. Working software is the primary measure of progress.
1. Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
1. Continuous attention to technical excellence and good design enhances agility.
1. Simplicity--the art of maximizing the amount of work not done--is essential.
1. The best architectures, requirements, and designs emerge from self-organizing teams.
1. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

## Sprint Planning
> Timebox: 1hr

Typically occurs on Monday. The planning begins with a retrospective of last sprint's productivity and completed stories. If there is rotating support, the role will be assigned to a point man, with optional backup. Depending on the team's methodology, there will then be a review of the backlog, covering any blockers, requests, or modifications to stories. As stated in [ShapeUp](https://basecamp.com/shapeup/webbook), there can assigning of members in small and big batches. Breadboarding with marker sketches, or web-based applications like [Figma](https://www.figma.com) can be used to create mockups and a general but not too specific outline of the task. 

![Agile Pivotal Tracker](/images/agile-pivotal-tracker.png)

## Standup
> Timebox: 1-2 min per member

* Try not to make it a roll call.
* Comment on performance metrics, and suggestions for improvement.
* Discuss and remove any blockers.
* Suggest pairing between developers.

## Pairing & Mobbing
> Timebox: As long as it takes

When pair programming, there is a `driver` and `navigator`. This is beneficial even early on in the recruiting phase, where the interviewer can share their screen so that the interviewee can dictate what code to write. In that sense, two heads are better than one, and solutions can be solved at a faster rate.

Mobbing involves multiple members of the team looking at the same codebase. While this can easily lead to holding up productivity, it can also lead to finding the fastest solution. 

## Code Review
> Timebox: Continuous

Favor asynchronous code review on platforms like [Github](https://github.com). Asynchronous meaning [Pull Requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) can be reviewed when time allows, barring any hotfixes or impediments.

* **Pull Requests**   
Can trigger CI tests to run. Pull Requests should be atomic, and commits in a manageable size. 
* **Milestones**  
The overarching goal that encompasses all the Pull Requests related to the story. Makes it easy to search for commits.
* **Tags**  
Indication on the status of the Pull Request. For example: `deploy dependency`, `review request`, `work in progress`, etc. 
* **Descriptions**  
Should include a link to the story in the backlog. Can contain a checklist of the remaining tasks, supporting screenshots, etc.
