I keep noticing this new pattern in how I work, think, and make decisions. Recently, it showed up so clearly that I felt it was worth writing down.                                                             
I was trained to think economically about software work. Count your operations, mind your memory, justify your complexity — Big-O thinking does not stay in the algorithms course, it shapes how you approach everything: automate and optimise. Now I keep automation and I learn to drop optimising. I have a vision for how I want to build and evaluate, and for the first time the friction is low enough to actually follow it. 

During my evaluation work, I realized I needed much more functionality in our pipeline to evaluate properly: API changes, additional outputs, the ability to stop the pipeline at specific points, freeze variables, continue from there, compare branches. Basically, a few good hooks in the right places.

The problem: this is not the codebase where I actively develop. It is a big repository with many modules, and honestly, it felt risky to touch it just for just a couple of experiments.

Still, I tried. I worked on it together with Claude Code, and in 3! hours we implemented everything I needed in one shot: API changes, extended config, hooks. 

My first thought was: previously this would have taken me 3–4 very intense days.
My second thought was: No, it would not have cost me 3–4 days.

I most likely would never have done it.

Not because it was impossible. Because the friction was too high to justify the experiment.

And that is the real shift for me.

AI does not just make work faster.
It changes what work becomes worth attempting.
And in evaluation, that matters a lot. Proper evaluation always wants more observability: intermediate outputs, replay points, branch comparison, frozen states.
Without support, you accept a crude setup. With support, you build the measurement infrastructure you actually need.

So no, the work is not necessarily less.

But it is deeper, more ambitious, and much more evidence-driven.

The productivity effect is not just compression of labor.
It is expansion of ambition.
