---
layout: post
title: Minecraft Mod Bootstrapping
---

I have been away all summer working an internship at certain tech startup. That is why I haven't posted anything lately. Anyways, I'm back now and have some time for some fun programming again.
  
What I have for you, today, is a quick class that I whipped up for Minecraft mod development that makes testing less annoying. It automatically loads a world that you can get into testing and not have to interact with the menu at all. If the world does not exist, it presents you with a create world GUI to make one. It does use Forge, but almost everything does these days.. Here is the gist:

{% gist cacb6ed1e9262cb5abf3 %}

You use it by instantiating it, and registering it with MinecraftForge.EVENT_BUS. Like this.

```
MinecraftForge.EVENT_BUS.register(new Bootstrap("WORLD_NAME"));
```

I would also recommend that you only register it on the client-side by using a sided-proxy.

This class is provided in the Public Domain, so you can do whatever the heck you want with it.