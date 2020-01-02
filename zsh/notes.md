_Written by: Reza Shams Amiri_
# from [zshrc · GitHub][ZG]

When you try to run lfcd() while having some input in terminal (e.g. skdjaskd), it will fail as the command run will be skdjaskd. Does anyone know the way to clear input in terminal before bindkey command is executed?

You need to invoke some other widget first to clear the line. You could use kill-whole-line but a better alternative is perhaps push-input. That puts the current line on a stack and it is popped next time a new command-line is started. It's often useful on it's own when you construct a complicated line and then want to quickly run something else first. Either way, if you're using bindkey -s, the sequence depends what keys those are bound to. For example:

    bindkey '\eq' push-input
    bindkey -s '^o' '\eqlfcd\n'
Alt-q is a common, albeit emacsy, binding for push-input. I use vi-mode but rebind a lot of the emacs widgets in the main (viins) keymap.

And for what it's worth Ctrl-O is commonly used for something like infer-next-history or accept-line-and-down-history which is really useful for repetitive steps like a git bisect or make, install, test steps.
* * *
Creation date: _2020-01-02_

[ZG]: https://gist.github.com/LukeSmithxyz/e62f26e55ea8b0ed41a65912fbebbe52