# babel-example

### Update of babel 7

Because the release of babel 7, there are two main changes you should know.

1. No more babel-core, babel-cli and babel-preset-env.  
Now babel 7 using **scope** to seperate different module of babel like @babel/core, @babel/cli, @babel/preset-env.  
That is, you should use yarn or npm to download **@babel/core instead of babel-core**.

2. There is no preset-es20XX like es2015, es2016 and other stages of preset.  
The only thing you need is @babel/preset-env which can offer what ever you need.

The more information about babel 7 is [here](https://babeljs.io/docs/en/usage), or [here](https://www.ithome.com.tw/news/125533) in chinese.

### Some keywords you must understand

**1. .babelrc** : It's a JSON file recording your setting about babel, usually you will see some keyword like "preset", "plugins".  
You need to add a file named .babelrc to your project directory, and the content is like below.
```=bash
{
    "presets": [
        "@babel/preset-env"
    ]
}
```
The only thing you need to remember is that **using "@babel/preset-env" on presets**.

**2. @babel/cli & @babel/node** : When you are developing, you should install @babel/cli on your computer by yarn or npm **Globally**.  
It will provide you command like "babel" and "babel-node" to compile files.

**3. @babel/core & @babel/preset-env** : When you want to compile any file by babel, you should install @babel/core and @babel/preset-env first. They provide every thing you need to compile or excute a file. Be noticed that you should install it locally. (Actually, you even can't install them globally.)

**4. @babel/polyfill** : You should add it to your project dependency for your client. They will need it to use command "node" to run files that you compiled by babel.

More detail in chinese is [here](https://code.kpman.cc/2016/09/13/babel-%E7%9B%B8%E9%97%9C%E5%90%8D%E8%A9%9E%E7%B0%A1%E4%BB%8B/).

# Installation

The first you should do is put **.babelrc** file to your project directory, then continue following the step below.

### For Developer :
Just like I mentioned, you should install **@babel/cli & @babel/node** on your computer by yarn or npm **Globally**.
```=bash
yarn global add @babel/cli @babel/node
// or
npm install @babel/cli @babel/node -g
```
Also, you will need **@babel/core & @babel/preset-env** for compiling.
```=bash
yarn add @babel/core @babel/preset-env -D
// or
npm install @babel/core @babel/preset-env -D
```

### For Client :

You should add **@babel/polyfill** as dependency for your client, they will need it to run file that be compiled by babel.
```=bash
yarn add babel-polyfill
// or
npm install babel-polyfill --save
```

# Usage

### @babel/cli

If you want compile file by babel, you should use something like:
```=bash
babel src/index.js -d build
```
After that, you also need to add one line to the file you just compiled.
```=bash
require('@babel/polyfill')
```
Then your client can use node to run the file.

By the way, you can directly run js file with babel too.
```=bash
babel-node src/index.js
```

### Production
If you follow the step of Installation correctly, then after cloning your project, your client only need to use these command
```=bash
yarn install --prod
// or
npm install -P

node build/index.js
```