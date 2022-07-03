---
title: "Emacs Multiple Dictionaries"
date: 2022-07-03T03:19:34+01:00
draft: false
tags: ["Emacs", "Programming"]
math: true
---

<!-- # Emacs Multiple dictionaries -->

Emacs is really a nice tool to work with if you are a developer or even a writer.
It's modes are incredibly versatile and never cease to amaze me.

Some days ago I found myself in a conundrum, my Emacs config only supported one dictionary at a time. 

## Dictionary Plugins
This dictionary plugins are really a life saver because they "lint" your text and help you find other words that are similar to the one you wrote incorrectly. Things that other code editors don't have for writing $\LaTeX$ or **Markdown**

This is very frustrating if you write school papers/essays in your home language and write something in other language. 

I would really take the effort of changing the dictionary language in my config every-time if there was no other way.
But I'm a **pro-programmer/procrastinator**, and we are known for spending hours over-engineering solutions to very simple problems.



_**This kept tormenting me in my sleep, I would wake up in cold sweat and to never sleep again!**_

Jokes aside, this problem was bothering me. But it came to me that the solution was pretty simple.
## Code
```elisp
(setq ispell-program-name "hunspell")
(setq ispell-dictionary "en_US,pt_PT")
(ispell-set-spellchecker-params)
(ispell-hunspell-add-multi-dic "en_US,pt_PT")
(setq ispell-personal-dictionary "~/.config/doom/.hunspell_per_dic")
```

or if you want to make sure it loads after ispell:

```elisp
(with-eval-after-load "ispell"
        (setq ispell-program-name "hunspell")
        (setq ispell-dictionary "en_US,pt_PT")
        (ispell-set-spellchecker-params)
        (ispell-hunspell-add-multi-dic "en_US,pt_PT")
        (setq ispell-personal-dictionary "~/.config/doom/.hunspell_per_dic")
)
```
## Why Hunspell
For those people asking: "Why are you using **Hunspell**? **Aspell** is much better"

Well, I am using **[Hunspell](https://hunspell.github.io/)** for this tutorial because it is still supported, Aspell has fallen down the pit of unsupported software. Besides, if LibreOffice uses it, it must be good enough for Emacs! 
