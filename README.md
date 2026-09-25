# 120hz-in-any-game-NOS
the name said it, 120hz in any game in Nothing OS. This guide will explain the relevant commands and Tasker + Shizuku automation to automate the whole process.

As we know it, Nothing OS locks every single game to 60hz except whitelisted ones. There's games like Geometry Dash, Hill Climb Racing, Minecraft, Hatsune Miku: Colorful Stage, etc. which support 120hz but are locked to 60hz because of the FPS cap on Android's side.

I made a little [writeup](https://gist.github.com/kinoosaki/ab25f9c5c330f32b87ecbe470856e8ab) regarding this and then I rebooted my phone. Was gone. I was like...do I have to run the commands everytime I reboot (see the gist). That's not so exhilarating.

So I went looking around, I'll admit I used GPT for this and it suggested something interesting: what if you use tasker + shizuku? I had forgotten tasker existed. I used its help to set it up and know the fundamentals. Rest of the tinkering and polishing was all me.

It's a very nice setup, it runs tasker + shizuku on startup and automatically executes the relevant command for every game you've configured so when you open it up. Means a reboot doesn't affect anything, it's persistent and works great. For every game that isn't working in 120hz by default, you can add it into tasker and it will work automatically.
