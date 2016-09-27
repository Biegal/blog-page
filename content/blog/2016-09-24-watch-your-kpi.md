---
author: "Marcin Biegała"
categories:
  - NoCode
date: "2016-09-24T13:35:31+02:00"
description: ""
title: "Watch your KPI"
type: "post"
---

Software development is not a piece of cake. While our languages and libraries are easier and more capable year by year, we still struggle with how to manage the whole process.  
So we leverage all kinds of techniques like short iterations, retrospectives etc. to improve that process, make it better step by step. But anyone trying to improve something will tell you that first you need to measure something to see if you can make progress.  
We're quite good in measuring things in code, we measure execution time, memory, number of users, transactions - the list goes on and on. But are we so clever when it comes to measuring our process?  
Before I start presenting various measurements or how managment likes to call them Key Performance Indicators, let's see quite popular quote by Eli Goldratt


*“Tell me how you measure me and I will tell you how I will behave. If you measure me in an illogical way… do not complain about illogical behavior…”*


Nice one, right? Keep that in mind for the rest of the article.


# Lines of code #
I've put it here just for the sake of completeness. I don't think anyone tries to use this metric in any way. It's dead simple, we count number of lines written by a developer. I hope I don't need to point out how dumb it is and leaves room for various abuses like extensive comments, obsessively descriptive code etc.

# Code coverage #
That's my favourite. Unit tests are helpful tool, I don't deny it. But with any unit tests, there is always a question of how much code coverage should we have in a project. We calculate it as a percentage of lines of code executed during unit tests to all lines in project.  
So what percentage should we aim for? I've heard here and there about 100%, 80% is more popular, 60% sounds like something reasonable.  
So what's the answer? It depends.  
Can a project with 10% coverage be 'better' than one with 70%? IMHO yes. Let's think for a moment what happens, when developers hear that 'they should have code coverage on level X' - they start writing tests (or change the job ;) ). And what they usually do, is that they write unit tests not for complicated parts of code that would benefit from few tests, but rather for code that is easily testable. So number of unit tests rises quickly, code coverage is getting higher, management is happy as they see pretty rising graph in some tool. Win? Partially. Every unit test comes with a burden. Anytime covered code changes, you need to update related tests. Sometimes you spend more time refactoring tests than changing the code.  
But they are helping - you would say! With tests it's safe to refactor!  
Remember what I wrote about developers writing tests for 'easier' parts of code?  
From my experience in 95% of cases tests fail not because logic is wrong but because someone forgot to update the test.
My advice is to stay reasonable using unit tests. Don't aim to get some random code coverage level that your manager came up with, instead think what parts of code are most crucial, which are most complicated, fragile and cover those areas. Fewer tests but covering right places in a project will be far more helpful than tons of tests checking if setting up variables works.

# Story Points #
I will start with a confession. This part can be a bit biased, as I'm not a fan of estimation. I'm not a fan of spending half of a day in a room or with headset, discussing if story is worth 2 or 3 story points. I know there are probably other advantages like better understanding of a story or sharing knowledge in a team, but that can be solved in other ways. We could try to write better story descriptions, leave comments about what were the problems with implementation etc. Have this knowledge written down somewhere as a point of reference, not as a quick chat no one will remember in few days. If we can add a responsive Product Owner to this, we could have pretty smoothly going project.
Ok, but what's wrong with the story points.  
So first of all, as I mentioned earlier they are often source of too long discussions. Should that be 3 or 5? S or M?But why bother at all? It's a task to be done. If it's at the top of the backlog or any other priority list it means it has to be done, no matter if it's a big chunk of work, or a simple thing.
Next thing with estimates is that they are random. I understand that for some simple and common things, it could be pretty accurate (in a specific project), but there is also a myth that people are getting better at estimating while project develops.  
For those looking a 'scientific approach' I'll send to this [blog post](http://toddlittleweb.com/wordpress/2016/03/14/to-estimate-or-noestimates-that-is-the-question-2/).  
One quote here: With the typically observed story point estimate accuracy range, our results show there is minimal added value to using velocity over using throughput for estimating purposes. When story size distribution is very large, then velocity has better predictive power than throughput. So if we try to have reasonably sized stories, there is little to none added value in puting a number to it, and we don't get better on it with time.  
Or in other words, as [@eldhash](https://twitter.com/eldhash) said:  
*"If I will take part in a lottery more often, does it mean I will win more and more?"*

# Velocity #
That's related with previous point. Velocity is handy value. It gives you an idea about how much work your team can do in a time period. But if we're setting this velocity as a goal, repeating over and over that we can 'not deliver a sprint' people will start thinking about numbers not a product. They will start to minimize work on a user story, won't refactor, won't innovate, because 'they could not deliver a sprint'. The question is, do you want nice, clean list of stories in Jira/Redmine/Axosoft or you want a product that is result of engagement and best ideas of your team?

# Time estimates #
I know we've took care of estimates already, but time estimates are such a special case, they need special attention. I've seen projects that required estimating user stories in story points, than dividing them into subtasks and estimating them in hours.  
That's just mean.I don't want to dwell too much, as I see this practice is used less every year, but in general it can end up in one of two ways. Both of them won't benefit your product.
One is developers, as clever beasts, will start to rise estimates to cover what's needed (and sometimes what's not too). Second, they will start cutting corners, minimizing effort, sacrificing quality.


# Number of bugs #
That's not very popular, but many projects track number of bugs found in a iteration/sprint/period of time. Logic here is simple: more bugs means worse performance. Remember the quote from the beginning? What developers will do, is they will start questioning every bug from testers team, trying to find someone else guilty. Others will just make an agreement with testers, that they won't fill a bug in a bugtracking tool, but rather just say it or send details over on slack. Bug will be fixed and management will be happy, that no bugs were found in software. That's a win!
What if we could embrace bugs? Encourage everyone to find more.  
Why?  
Because that means we've found them before our users and having enough data, we could find places that are 'hot zones' in our codebase and could benefit from some refactor (or unit tests).


Let's leave IT world for a minute and teleport to a beautiful world of coffee.  
Imagine you visited a coffee shop nearby and barista prepared a fresh and tasty coffee from aeropress. You loved it so much that first thing you did after getting home was to order same Aeropress and same coffee they had in a coffee shop. So you got your Aeropress and coffee, you've found a recipe on the internet. You get exact weight of coffee beans, grind them to proper degree, pour exact amount of water and… It doesn't taste as good as the one you had day before.   
So did barista have different recipe? No.  
Better tools ? No.  
What he add, was that 'special ingredient', he put focus, experience and engagement. That made your coffee so delightful. Same rule applies to software. Numbers, checking off tasks and blindly following common measures won't guarantee success. You must have a team of people willing to give that 'special ingredient', a spark.

&nbsp;  
So now what? Are we doomed and only anarchy will rule? No, there are other things to look at.  
First of all, do you feel your product is successful?  
Does number of users increase? Do they send you positive feedback?  
If yes, then probably your doing good job. Now look at your team, do you struggle with people complaining and leaving your company all the time or are they happy and engaged?
That's even better!

So don't manage your project from Excel or charts in Jira, talk with your customers, talk with your developers - if they are all happy, you are on a good way to success.
