---
layout: post
title: "Workaround: Failed to import unicodedata in Sublime Text 2 under Windows"
date: 2012-10-25 13:36
categories: IT
tags: [Sublime Text 2, Python]
---

It's weird, while importing some .pyd modules, like pyexpat, unicodedata in Windows version of [Sublime Text 2](http://www.sublimetext.com/2), you will get ``ImportError``, for example:

``` python
import unicodedata
```

Will result in:

``` plain
Import Error: No module named unicodedata
```

However, since standard pyd modules are not missing, reside correctly in the same folder as sublime_text.exe, we can add that folder to sys.path in order to allow embedded python interpreter to load these modules:

``` python
sys.path.insert(os.path.dirname(sys.executable))
```

After that, you can import these standard python modules without pain, I hope it's useful for Sublime Text 2 packages developers who met the same problem before.
