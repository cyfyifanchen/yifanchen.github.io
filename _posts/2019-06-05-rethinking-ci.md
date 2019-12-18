---
title: "Rethinking CI"
layout: post
date: 2019-6-05
tag:
- dev
blog: true
star: false
---

<span class="fl">C</span>I, Continuous Integration, is a term mostly used in software development, meaning a certain workflow is expected to achieve Continuous Integration, ideally resulting in a smooth, healthy and rapid software development workflow. CI, however, is not being used properly if you don’t understand it right, it could become procrastination.

I was in a team seeing that most developers got stuck while using CI, in this case, git workflow, and not be able to move on to the next action. The end result of a non-proper git workflow is inefficiency. So, I thought about sharing some of my experiences here.

I was working on a task the other day when I got ready to commit in my code and waiting for it to be pushed to production. The process that I had to go through was finding someone to review my code, so I slacked a  message in the general channel, and hopped someone could just open the link from my message and click the approve button, nothing more than that. I eagerly waited like 10 minutes, and no responses, then I stood up and thought about getting a cup of a coffee. "Maybe others are busy at this time, getting a cup of coffee should be able to do it" However, still no responses after another 10 minutes when I got back. "Man, do I have to @ someone every single time, I hate to interrupt others for such a small thing." Well, for the process to go, it left me no choice. So I did, I @ a guy who sits by me, and impatiently explained the code change to him, I could tell that he couldn't care less about the code quality and just wanted to get the process off of his hand. So he could jump back to what he was doing, he clicked approve, then the process carried on. You see, at this point, no one is doing the job right, on my part, I was quite eager. On his part, he just wanted to do what he was doing. We both rushed the process without even thinking. Which is opposite of the purpose of code review. And, this is a part we must go through every single day, it wastes time from both parties.

If a workflow becomes something like this, we need to change it. There's no one size fits all solution. Google's best practices of code review is a guide to follow, on the other hand, if you follow it blindly, it ends up wasting a lot of time.
