# 120hz-in-any-game-NOS
the name said it, 120hz in any game in Nothing OS. This guide will explain the relevant commands and Tasker + Shizuku automation to automate the whole process.

As we know it, Nothing OS locks every single game to 60hz except whitelisted ones. There's games like Geometry Dash, Hill Climb Racing, Minecraft, Hatsune Miku: Colorful Stage, etc. which support 120hz but are locked to 60hz because of the FPS cap on Android's side.

I made a little [writeup](https://gist.github.com/kinoosaki/ab25f9c5c330f32b87ecbe470856e8ab) regarding this and then I rebooted my phone. Was gone. I was like...do I have to run the commands everytime I reboot (see the gist). That's not so exhilarating.

So I went looking around, I'll admit I used GPT for this and it suggested something interesting: what if you use tasker + shizuku? I had forgotten tasker existed. I used its help to set it up and know the fundamentals. Rest of the tinkering and polishing was all me.

It's a very nice setup, it runs tasker + shizuku on startup and automatically executes the relevant command for every game you've configured so when you open it up. Means a reboot doesn't affect anything, it's persistent and works great. For every game that isn't working in 120hz by default, you can add it into tasker and it will work automatically.

Let's start. For this I used [thedjchi's Shizuku fork](https://github.com/thedjchi/Shizuku) which has a ton of fixes and functionality over the stock Shizuku app and is the best one I have found so far.

<img width="429" height="951" alt="scrcpy_jsu2JxTdrz" src="https://github.com/user-attachments/assets/0c34a22a-b56f-4363-8daf-1293937ff73c" />

Of course, do the standard stuff like disabling battery optimizations and turn on the Shizuku service and connect with adb.

Next, make sure these 3 are on in the settings. You can see what the rest are doing. The watchdog is merely a service that just sees if Shizuku is running and notifies you accordingly, which is handy.

<img width="429" height="951" alt="scrcpy_k5LjyAApIi" src="https://github.com/user-attachments/assets/2bdf560f-2184-4622-a5a6-9f8b2bd13d41" />

Before we get into tasker, go to misc section in settings and turn this on. It makes life slightly easier, you won't have to tick it manually everytime you create a task for the relevant game. I prompt should come up to grant permission to tasker to use Shizuku. If not here, it should come when you make the task. Either way if you see it, give the permission!

<img width="429" height="951" alt="scrcpy_Y8DGA8a3gv" src="https://github.com/user-attachments/assets/2af7345b-6d95-4ef6-8c34-2ed845ed752b" />

Tap on the plus button you see at the bottom right, and then tap on "create" when this popup comes up. You can tap on "stop reminding" and it won't come up in the future.

<img width="429" height="951" alt="scrcpy_1nH64eJVT8" src="https://github.com/user-attachments/assets/420b1fd0-365c-4ebb-998f-4939ddedc409" />

Next tap on "applications"

<img width="429" height="951" alt="scrcpy_I3xN9eaz3k" src="https://github.com/user-attachments/assets/3ab15d11-c1bd-459f-891d-10ede25c72c7" />

Tap on the game you want to run at 120hz and then go back. We're using Geometry Dash here as an example.

<img width="429" height="951" alt="scrcpy_vL2j0WKcUK" src="https://github.com/user-attachments/assets/b7be129b-0f67-406a-8f0f-da452f755429" />

Tap "new task" here

<img width="429" height="951" alt="scrcpy_AxhnKxG1mJ" src="https://github.com/user-attachments/assets/d135175b-1b99-43e7-87d6-09ee4832b28e" />

Tap on the plus button here

<img width="429" height="951" alt="scrcpy_5qOrNgyXxX" src="https://github.com/user-attachments/assets/2c054303-5a5c-45dd-a511-b27413cf6c81" />

(the list will be longer for you lmao as I used the search feature like you can see) Tap on "run shell" here.

<img width="429" height="951" alt="scrcpy_U4C8p7rBuQ" src="https://github.com/user-attachments/assets/d4d22d1b-039d-408d-b16d-ea514c989568" />

Put in `cmd game set --fps 120 packagename` (`packagename` is the package name for the game you're doing this for. You can open the app info and then scroll to the very buttom to see the package name and version) as the shell command. If you didn't tick "Shizuku in Run Shell By Default" you can turn it on here, there is an option on this page but I haven't included it in the screenshot. Something along the lines of "Shizuku in Run Shell".

<img width="429" height="951" alt="scrcpy_XMObMzye4h" src="https://github.com/user-attachments/assets/895c9700-29bd-4a66-b590-e9c9868258b6" />

That's it! You can follow the steps in tasker for every game you want 120hz on. It will work immediately. On reboot, tasker starts automatically, shizuku starts too and a prompt will come up by Android asking you to select the network or something to turn on Shizuku, select your network and it will start up automatically.
