# react-native-
iOS集成react native时遇到的常见的问题列表

The frequently encountered problems in integrating React Native with existing iOS project

目标观众：OC程序员，但不了解或对JS了解很少

Target Audiences: OC Programmers, but only have a superficial knowledge about JS and React Native

# Server Side Problems

## Server Environment Setup

我们已知，运行的iOS应用从远端服务器端下载js bundle，所以在开发阶段，我们通常需要一个本地的服务器代替远端服务器来服务运行在Mac上的仿真机或iPhone上的应用。

React Native采用Node.js作为服务器容器，所以在Mac上我们应该安装npm（node package manager）.这个工具负责了node服务器的启动、关闭，第三方库、依赖的管理，脚本命令的执行等等。

打开一个终端，输入
```
    brew install node 
    brew install watchman
```
node安装完成，继续输入
```
    npm install -g react-native-cli
```

这个命令安装了react native 命令接口，-g参数是必须的，这保证了该接口对Mac上的所有react native项目可用。

As we already know, the running iOS app downloads JS bundle from remote server, so in development phase, we need a local server to serve the app which is running on the Mac  (e.g simulator) or on the iPhone.

React Native adpots Node.js as the server container, so on Mac we should install npm (node package manager), which is responsible for the server startup and shotdown, third party libraries and dependencies installation and removement, script command execution and so on.


open a Terminal, we input

```
    brew install node 
    brew install watchman
```

After node is installed, we tap below command in Terminal
```
    npm install -g react-native-cli
```

this command installs react native client command line interface, the -g argument is indispensable, which guarantees that the react native cli is available for all react native projects on the Mac.

more details please reference: https://facebook.github.io/react-native/docs/getting-started.html#content

## JS Editor installation

Facebook为编辑器Atom发布了一款名为Nuclide的插件，这不是必须的，但强烈建议iOS开发者安装，Nuclide包含了React Native相关功能和Facebook自己为js添加的类型检查（通过flow），使用flow后，所有的js代码必须显示加上类型。  

Facebook launched a great plugin Nuclide for the charming editor Atom, this is optional, but I strongly recommend iOS developers to use this editor and its plugin, because in Nuclide Facebook play an additional type checking on JS code (flow), when using flow, all code in JS must add type explicitly.  


To download Atom, please reference: https://atom.io/  


After Atom is installed, we launch it, go to Atom->Preferences...->Install and tap Nuclide in the search box, the top 1 result is from facebook, and we install it.  


![atom install nuclide](./images/atom_install_nuclide.png)

Now, we restart it, we can see additional Nuclide entry on the tool bar of atom.
![atom nuclide installed](./images/atom_nuclide_installed.png)

## Project Integrating

It's not rare to have an existing project, so instead of creating a total new React Native project, we should add existing iOS project to React Native folder(same process apply to Android)  

A React Native Project looks like below:

![react native project](./images/react_native_project.png)

In ios folder, we store our existing iOS project(android folder for storing android project)  

index.ios.js is the entrance file of our js code for iOS(the counterpart file for Android is index.android.js)  

Here we should pay special attention to package.json and node_modules folder.  

We don't create node_modules folder, which contains the React Native code and all of its' dependencies code including js code and oc code.  

Instead we edit package.json, an ordinary package.json looks like below:  

![package json](./images/package_json.png)  

name specify our project name(refer to the project name in info.plist of Xcode)  

version specify the version of the project (refer to the version value in info.plist of Xcode)

scripts specify the abbreviation of the long command, which will be called by npm

e.g 

in Terminal, we tap  
```
    npm start
```

which will be substituted by  
```
    node node_modules/react-native/local-cli/cli.js start
```

in dependencies section, we specify the version of react(15.4.1) and react native() we use




# JS Problems



# OC Problems



