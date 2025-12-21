# anti-steam-commonredist

<details><summary>Intro</summary>
You are a sysadmin w/ 10+ years of experience.
Bloated Windows image is trimmed the minimum, with .NET 3.5, vcredist, printer patch et al. packed.

You have a happy life.

Now you install the *de facto* go-to gaming platform on PC, which finally goes 64-bit in 2026, despite still having a 32-bit service vulnerable to local privilege escalation.

You install your good old game, and,

all of a sudden, since you have 1000Mbps network,

a warning pops up reminding you Steam attempted to install a runtime you've packed already, and failed.
You become angry, as it's the I-dunno-probably-60th time Steam  offend you this way.

So you spent 10 minutes searching and wrote a script to prevent Steam from installing commonredist, and 30 minutes later realized it could be done via registry.

That's the birth of anti-steam-commonredist.

![Well, of course I know him. He's me.](/res/well.avif)
</details>

## Variant

[no-really-common-redist.reg](/reg/no-really-common-redist.reg) is recommended as OpenAL/PhysX/XNA are rarely used nowadays and chances are you can't find an installer more trustworthy than the one Steam provides.

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

Only tested on x86_64 Windows 10/11 system, arm is not guranteed to work.

If you use regular user without administrator privilege, change `HKEY_LOCAL_MACHINE` (aka. HKLM) to `HKEY_CURRENT_USER` (aka. HKCU) before importing. Keep in mind you need to do it for *every* user with Steam access on your system.

This only prevent Steam from installing commonredist, those runtime still need to be installed.
Personally I recommend [vcredist](https://github.com/abbodi1406/vcredist/releases/latest), or just install from any package manager you like: winget, chocolatey or scoop.

For more details (TBH there is none), check my blog post [阻止 Steam 安装 Windows 运行库](https://blog.vinfall.com/posts/2023/08/anti-steam-commondist/).
