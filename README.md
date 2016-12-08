#hubot

Hubot Installtion on Ubuntu

1. Introduction
If you ever wanted to have a personal robot then you are reading a correct article. This tutorial is a brief demonstration on how easily you can configure your personal or company robot, then soon after, connect it with one of available adapters like: shell, campfire, hipchat, irc, gtalk or skype. In this tutorial I'm going to teach you how to set up Hubot with its default adapter Shell. Although it's the simplest option, it's the solid foundation for your future modifications. 
Correctly configured and connected Hubot can dramatically improve and reduce employee efficiency as well as give your company lots of fun. Additionally, It can provide your team with the newest rss feeds or send crucial notifications. Keep in mind, that Hubot is developed by Github team, so it's next pros for spending a while on investigations.

2. So what is Hubot ?
Hubot is open source, written in CoffeeScript on Node.js. It can be easily deployed on PaaS platforms like Heroku. Hubot comes preinstalled with several core scripts like math, ping, help, translate or youtube. 
Additionally you can visit community repository which provides tons of other interesting scripts (i.a: ascii, coin, deploy, dice or jenkins). If this list still doesn't meet your expectations, feel free to write your own script using CoffeScript. 
As a starter I wanted to present few examples which I hope will bring some light to this topic.

Hubot> hubot convert me 56MB KB
Hubot> 57 344 kilobytes
Hubot> hubot mustache me linuxconfig.org
Hubot> http://mustachify.me/2?src=http://img1.tuicool.com/aqi6r52.jpg#.png
Hubot> hubot translate me praktyczne
Hubot> "praktyczne" is Polish for " Practical "
Hubot> hubot image me niagara falls
Hubot> http://www.niagarafallslive.com/images/HorseshoefromSkylon.jpg#.png
Hubot> hubot convert me 5 years days
Hubot> 1 826.21099 days
Hubot> hubot math me 2(3+7)/4
Hubot> 5
Hubot> hubot die
Hubot> Goodbye, cruel world.
The below screen-shot illustrates basic Hubot commands:



Hubot with Hipchat adapter, help command

3. Configuring Ubuntu for Hubot
Before I give you detailed instruction how to configure Ubuntu for Hubot, let's create the list of prerequisites:

node.js environment
node package manager
git, coffee and cake commands
3.1. Install Ubuntu
Install Ubuntu Desktop 32-bit 12.04 LTS.

3.2. Update Repositories
First of all, after Ubuntu installation is finished, update all your repositories for latest packages:

$ sudo apt-get update
3.3. Install Prerequisites
Then make sure you have build-essential package.

$ sudo apt-get install build-essential
4. Install Node.js
It's high time to install Nodejs environment so I suggest to pick up the newest stable version for Ubuntu. First of all check your current situation:

$ sudo apt-cache show nodejs | grep Version
You will probably see 0.6.12~dfsgq-1ubuntu1, which is rather old. It would be much better to use newer version, so add private repository by doing:

$ sudo add-apt-repository -m ppa:chris-lea/node.js 
In case,you don't have add-apt-repository command, please do:

$ sudo apt-get install python-software-properties
If you see /etc/apt/sources.list.d/chris-lea-node_js-precise.list file, it means you've added it correctly. Next, update all your repositories again and download everything from chris-lea personal package archives with:

$ sudo apt-get update
From now on you are ready to install the freshest Nodejs version for Ubuntu with the simple command:

$ sudo apt-get install nodejs
Check its version by running:

$ node -v 
then try to create simple script that sets up http server to prove your former actions.

cat > ~/server.js <<EOF
var http = require('http');
http.createServer(function (req, res) {
res.writeHead(200, {'Content-Type': 'text/plain'});
res.end('Hello World\n');
}).listen(1337, "127.0.0.1");
console.log('Server running at http://127.0.0.1:1337');
EOF
Next, after running node ~/server.js, visit your favorite browser and type in following url: http://127.0.0.1:1337. You should spot Hello World text, which indicates that you've installed Nodejs correctly.

You will also need to install node package manager for easy management of all nodejs' modules.

$ sudo apt-get install npm
From now on you should be able to run:

$ npm -v
5. Hubot Installation
Before you install Hubot, you'll need git, the distributed source code management system. Just do the simple command:

 $ sudo apt-get install git-core
and you are ready to clone all public repositories that Github hosts. Those and many more.

It's high time to install Hubot robot, so let's do that! Install all needed packages by doing:

$ sudo apt-get install libssl-dev redis-server libexpat1-dev
With use of node package manager, you will also need to globally install coffee and cake terminals.

$ sudo npm install -g coffee-script
Since now, you can use coffee and cake commands across all your ubuntu installation. It's high time to download the latest Hubot source code from Github. I've decided to put it there:

$ cd /opt && sudo git clone git://github.com/github/hubot.git
what creates /opt/hubot folder. Next, use node package manager to download all needed libraries that Hubot is based on by doing:

$ cd /opt/hubot && sudo npm install 
You can also search and learn more about packages through exploration of npm registry website. In meantime, once installation process is done, run this from /opt/hubot working directory:

 $ npm ls 
and soon you should see the package tree similar to the one below.

hubot@hubot-nest:/opt/hubot$ npm ls
hubot@2.3.4 /opt/hubot
├── coffee-script@1.3.3
├─┬ connect@2.3.4
│ ├── bytes@0.0.1
│ ├── cookie@0.0.4
│ ├── crc@0.2.0
│ ├── debug@0.7.0
│ ├── formidable@1.x.x
│ ├── fresh@0.0.1
│ ├── mime@1.2.4
│ ├── qs@0.4.2
│ └── range-parser@0.0.4
├── connect_router@1.8.6
├── log@1.3.0
├── optparse@1.0.3
└── scoped-http-client@0.9.7
If your answer to Do you wish to have your own personal robot? question is affirmative, please run:

 cd /opt/hubot && ./bin/hubot 
and in the twinkling of an eye you will land up in Hubot terminal where you can play around.

Hubot> hubot echo “I did it”
Hubot> hubot who is Hubot
The best way to discover all the hubot options is by typing:

Hubot> hubot help
Once you become familiar with hubot commands and basic scripts, you will be able to convert values, do simple math calculations or search for images with google. You'd be able to see youtube movies, specify locations on google maps or even draw mustaches on somebody's picture like it was shown on screen-shots before. By teaching your robot more scripts, you will soon see how to convert the text to ascii or greet somebody with beer. This and many more features are awaiting you.

6. Conclusion
It's just the tip of the iceberg. The source code of Hubot is being constantly updated, so you can follow its repository changes on Github. You can also check its Wiki page to see how many adapters were written so far. If you managed to test other adapters than Shell or Hipchat before me, I'd gladly listen to your feelings and tips.

7. Custom scripts

Copy coffee scripts under scripts directory to start using them. More information on hubot scripting can be found @https://github.com/github/hubot/blob/master/docs/scripting.md  and examples can be found @https://github.com/github/hubot-scripts
