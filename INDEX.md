---
title: "EzPing"
permalink: /
layout: default
---

# EzPing Summary 🚫
[EzPing](https://ezping.gg/) is a .NET C# application that claims to improve your ping for competitive gaming, primarily targeted towards Minecraft players. It is an **overpriced scam** with a lot of claims that do not make any sense, [I recommend you to watch this video first](https://www.youtube.com/watch?v=tyhVoeyi4r8). In summary, a YouTuber called [Ziblacking](https://www.youtube.com/c/Ziblacking) actually is behind EzPing and he has a bad reputation for scamming, generally being very clickbaity and cheating. Here is a list of what EzPing does from simple analysis with [ILSpy](https://github.com/icsharpcode/ILSpy) and [RegistryChangesView](https://www.nirsoft.net/utils/registry_changes_view.html):

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

### Conclusion - Do not buy this program!
Overall, EzPing does nothing worth the money. Setting process prorities (especially to real-time) does nothing for network stability or ping and causes issues with system responsiveness. TCPNoDelay is already hard-coded within Minecraft and can be set via applications like TCPOptimiser system-wide or you can manually set easily. You can learn how to set DSCP policies in Windows by [clicking here](https://en.wikipedia.org/wiki/Differentiated_services) and you can literally just close your web browser or other apps using bandwidth whilst gaming instead of blocking all apps via Windows Firewall. For your information, Minecraft uses little bandwidth and so does any idle applications in the background. Whilst writing this guide on an almost default Windows 11 installation with Discord in the background, there's pretty much no bandwidth being used.

Applications in Windows can not alter your Windows networking settings (whilst maintaining the same amount of ping) to reduce your knockback or increase your reach, it simply doesn't work like that.

**Note:** Although there's a refund and a free trial, people experience placebo, which means they pay long term for a pointless program.

### An actual guide to follow
If you want to actually configure your network settings properly, [follow this guide](https://github.com/djdallmann/GamingPCSetup/blob/master/CONTENT/DOCS/NETWORK/README.md) with proven and free tweaks. Although, I can not guarentee that it will help with ping or other network issues. It won't give your extra reach or less knockback in Minecraft either, unless your ping somehow changes a lot after following the guide, which is very unlikely.

Website, repo and research done by [he3als](https://github.com/he3als).
