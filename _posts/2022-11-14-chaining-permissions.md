---
layout: page
title: Chaining Permissions
tags: linux
---

# Chaining Permissions

In chaining permissions we give simultaneous permissions to different sets be it user or groups or others.

__Example__:
```bash
chmod u+rw,g=r,o= family_dog.jpg
```

Here we can see that we gave user read and write permission and gave group read permission and nothing to other users. This is how we chain permissions in one command.  


