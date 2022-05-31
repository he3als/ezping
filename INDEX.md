---
title: "EzPing"
permalink: /
layout: default
---

# EzPing Summary 🚫
[EzPing](https://ezping.gg/) is a .NET C# application that claims to improve your ping for competitive gaming, primarily targeted towards Minecraft players. It is an overpriced scam with a lot of claims that do not make any sense, [I recommend you to watch this video first](https://www.youtube.com/watch?v=tyhVoeyi4r8). In summary, a YouTuber called [Ziblacking](https://www.youtube.com/c/Ziblacking) actually is behind EzPing and he has a bad reputation for scamming, generally being very clickbaity and cheating. Here is a list of what EzPing does from simple analysis with [ILSpy](https://github.com/icsharpcode/ILSpy) and [RegistryChangesView](https://www.nirsoft.net/utils/registry_changes_view.html):

- Sets [DSCP policies](https://en.wikipedia.org/wiki/Differentiated_services) for games (does not do this correctly so all of the policies are useless)
  - Dependant on people's situation with networking
  - Tells the router to prioritise certain packets
  - Probably won't even help with ping, unless your network is congested
- Sets process priorities (sets the service group for BITS to real-time and selected processes/games in the app)
  - Setting any process to real-time is stupid, unless you exactly know what you are doing and you are not actively using your PC
  - Setting Minecraft to real-time or other process priorities won't help with ping, it only effects the CPU and it causes issues
  - Setting any intensive process to real-time worsens responsiveness significantly 
  - Doesn't even help performance most of the time
  - Windows Game Mode or Process Lasso handles priorities well, so you don't need EzPing to do this crappily
- Sets TCPNoDelay
  - Can cause throughput issues, again, another tweak dependant on multiple variables
  - Minecraft controls if TCPNoDelay is enabled or not, it completely ignores the registry
  - 1.8.1+ vanilla already has TCPNoDelay enabled and pretty much all clients have TCPNoDelay enabled
  - TCPNoDelay disables [Nagle's algorithm](https://en.wikipedia.org/wiki/Nagle%27s_algorithm)
- For the ranked mode, sets firewall rules to block every app from accessing the internet
  - Causes an issue with Windows Defender (Defender flags the firewall rules)
  - Most of the time it won't even help, Minecraft uses very little bandwidth and most likely it will be the same with apps in the background
  - You can just close your web browser or whatever is taking up bandwidth... Windows processes will not take up a bunch of bandwidth, you don't need to spend 8 pounds a month on a scam for this

**Note:** Although there's a refund and a free trial, people experience placebo, which means they pay long term for a pointless program. 

**Do not buy this program!**
