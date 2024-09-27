## Intro

You are a sysadmin w/ 10+ years of experience.
Bloated Windows image is truncated to as minimum as possible, with .NET 3.5, vcredist, printer patch *et al.* packed.

You have a happy life.

Now you install the *de facto* go-to gaming platform on PC, which is still 32-bit as of 2024, and comes with a service vulnerable to local privilege escalation.
You install your good old game, and,

all of a sudden, since you have 1000Mbps network,

a warning pops up reminding you Steam attempted to install a runtime you've packed already, and failed.
You become angry, as it's the I-dunno-probably-50th time Steam try to offend you this way.

So you spent 10 minutes searching and wrote a script to prevent Steam from installing commonredist, and 30 minutes later discovered it could just be done via registry.

That's the birth of anti-steam-commonredist.

![Well, of course I know him. He's me.](/res/well.avif)

## Variant

[no-really-common-redist.reg](/reg/no-really-common-redist.reg) is recommended as OpenAL/PhysX/XNA are rarely used nowadays and chances are you can't find an installer more reliable than the one Steam provides.

| Variant | Blocked content |
| ------- | --------------- |
| [no-directx.reg](/reg/no-directx.reg) | DirectX |
| [no-dotnet-framework.reg](/reg/no-dotnet-framework.reg) | .Net Framework |
| [no-vcredist.reg](/reg/no-vcredist.reg) | vcredist |
| [no-really-common-redist.reg](/reg/no-really-common-redist.reg) | .NET, DirectX & vcredist |
| [no-steam-commonredist.reg](/reg/no-steam-commonredist.reg) | .NET, DirectX, vcredist, XNA, PhysX, OpenAL |

## Usage

0. As a general reminder, **ALWAYS** backup your registry before messing with it!
1. Download your favored variant, **backup registry**, import registry, done.

## Reminder

This is only tested on 64-bit Windows 10/11 system.
32-bit system is not supported, but you may change `HKEY_LOCAL_MACHINE\SOFTWARE\WOW6432Node\Valve\Steam\Apps\CommonRedist` to `HKEY_LOCAL_MACHINE\Software\Valve\Steam\Apps\CommonRedist` and give a try.

If you use regular user without administrator privilege, change `HKEY_LOCAL_MACHINE` (aka. HKLM) to `HKEY_CURRENT_USER` (aka. HKCU) before importing. Keep in mind you need to do it for *every* user with Steam access on your system if so.

This only prevent Steam from installing commonredist, those runtime still need to be installed.
I recommend [vcredist](https://github.com/abbodi1406/vcredist/releases/latest), or alternatively if you use package manager like winget, Chocolatey or Scoop, just install from that.

For more details (TBH there is none), check my blog post [阻止 Steam 安装 Windows 运行库](https://blog.vinfall.com/posts/2023/08/anti-steam-commondist/).
