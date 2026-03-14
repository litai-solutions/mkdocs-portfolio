I keep noticing this new pattern in how I work, think, and make decisions. Recently, it showed up so clearly that I felt it was worth writing down.

I was trained to think economically about software work. Count your operations, mind your memory, justify your complexity — Big-O thinking does not stay in the algorithms course, it shapes how you approach everything: automate and optimise. Now I keep automation and I learn to drop optimising. I have a vision for how I want to build and evaluate, and for the first time the friction is low enough to actually follow it.

During evaluation work I realized I needed much more functionality in our pipeline: API changes, additional outputs, the ability to stop at specific points, freeze variables, continue from there, compare branches. A few good hooks in the right places.

The problem: this is not the codebase where I actively develop. A big repository with many modules — honestly, it felt risky to touch it for a couple of experiments.

Still, I tried. Together with Claude Code, we implemented everything I needed in one shot. The whole cycle: implementation, tests, build, verification took about 3 hours.

My first thought: this would have taken me 3–4 very intense days before.

My second thought: No, it would not have cost me 3–4 days. I most likely would never have done it! The friction, fear, and repository overhead were too high to justify the experiment.

That is the real shift for me. AI changes my judgment of what work is worth attempting. 
And this is work I wanted to do before, but usually decided was too invasive, too risky, or too expensive in time and mental load.

In evaluation this is especially true — good evaluation always wants more hooks, more intermediate outputs, replay points, branch comparison, frozen states. Without support, I accept a crude setup. With support, I build the measurement infrastructure I actually need and can answer hard questions based on data. So much more confidence.

For me, the productivity effect is not compression of labor. It is expansion of ambition.