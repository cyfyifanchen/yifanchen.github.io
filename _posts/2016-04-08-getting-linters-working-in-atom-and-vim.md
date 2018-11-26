---
title: "Getting linters working in Atom and Vim"
layout: post
date: 2016-04-08 
tag:
- vim 
- atom
- linters
blog: true
star: false
---

## Getting linters working in Atom and Vim

I like [code consistency]({{ site.url }}/The-Value-of-Code-Consistency-is-Underesimated/){:target="_blank"}, and think the value of it matters a lot to a team in a long run. It's not easy to achieve code consistency in the middle of an ongoing project. What's even harder is that finding a doable approach of getting same code style of everyone in the team. To complete this for the team, there will be fine training and strict rules needed. However, lack of proper training and code style management are obviously everywhere today. There is a fine line between killing the creativity of developers and boosting the productivity of teams. Software development is not about one single kick ass developer, it's about teamwork and team effort. I decided to give a try.

If I happen to have an idea that hopefully my team will adopt, I have to make sure first the value of the idea is beneficial to the team in every aspect. Second prototype happens before implementation. Then the rest of the team only needs to spend a minimal effort to carry on. To do so, I need to find out how to do the following:

+ Finding the correct litners
+ Making sure the linters work in both Atom and Vim, possibly all common text editors.
+ Convince the team

#### Part 1 - Finding the correct linters

Of course, the easiest part comes in first. Finding suitable litners isn't hard. [Airbnb](https://fortune.com/2015/12/09/airbnb-glassdoor/){:target="_blank"} is rated the best tech company to work for in 2016. I happen to know Airbnb because of their linters, not the service I used. Airbnb has several linters, the most famous and beloved linter is their [JSCS linter](https://github.com/airbnb/javascript){:target="_blank"}.
It is open-sourced, and very popular among developers. I dug in a little and read through the documentations, made sure it was what I was looking for and simple enough for my team to use.

#### Part 2 - Making sure the linters work in common editors

I browsed [JSCS](https://jscs.info/){:target="_blank"} for the info I needed. Bam, I found everything [here](https://jscs.info/overview){:target="_blank"}. I opened Atom and installed the
[JSCS Linter](https://atom.io/packages/linter-jscs){:target="_blank"} inside Atom, changed the preset to Airbnb. Tested it with couple `js` files, it worked beautifully. Then let's get it working in Vim. Although I am a Vimmer, but I know it will take much longer to make it working in Vim than in Atom. First, I needed to `npm insteall jscs -g` to my `home` directory. Then I created `.jscsrc` file and put the preset like the following code in my `home` directory.

    {
      "preset": "airbnb"
    }

Then, the rest is to config Syntastic to call the correct litner.

    set statusline+=%#warningmsg#
    set statusline+=%{SyntasticStatuslineFlag()}
    set statusline+=%*
    
    let g:syntastic_javascript_checkers = ['jscs']
    let g:syntastic_html_tidy_exec = 'tidy5'
    let jshint2_read = 1
    let jshint2_save = 1
    let g:syntastic_check_on_open = 1
    
    "dispaly all errors for mutiple checkers
    let g:syntastic_aggregate_errors = 1

Good, everything worked. Although Syntastic with new linter slows down Vim loading speed a bit, I am still pretty happy with the result of it. The next step is getting CSS and React linters working, and put them in our build system, which I will write later.


#### Part 3 - Convince the team

Luckily, everyone in my team is a team player. It doesn't take much to explain the value of it. It's especially easier since I have figured out everything first, all they need to do is execution.

#### Conclusion

This is a post showing how I took an idea and applied it to my team. In reality, it might be harder to adopt an impractical idea or your team is too big to change. However, a little by little everyone can improve their teams, everyone can be a true team player.



