---
Title: Git hacks
Description: 
Date: 14-02-2021
Tags: #git
References: 
Editor: markdown
---

# Git hacks
### Permanently cache the git credentials
```git
git config --global credential.helper store
````

### porcelain
Porcelain" is the material from which toilets are usually made (and sometimes other fixtures such as washbasins). This is distinct from "plumbing" (the actual pipes and drains), where the porcelain provides a more user-friendly interface to the plumbing. *:)*

Git uses this terminology in analogy, to separate the low-level commands that users don't usually need to use directly (the "plumbing") from the more user-friendly high level commands (the "porcelain").

The interface (input, output, set of options and the semantics) to these **low-level commands are meant to be a lot more stable** than Porcelain level commands, because **these commands are primarily for scripted use**.  
The interface to Porcelain commands on the other hand are subject to change in order to improve the end user experience.

```bash
#examples
git status --porcelain
git push --porcelain
git blame --porcelain
```


Obsidian references: 