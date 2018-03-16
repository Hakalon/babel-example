# babel-example

 There are three words you should know before using babel.

**1. .babelrc** : It's a JSON file recording your setting about babel, usually you will see some word like "preset", "plugins".  
You need to add a file named .babelrc to your project directory, and the content is like below.
```=bash
{
    "presets": [
        "env"
    ]
}
```
At first, the only thing you need to remember is that **using "env" on preset**.

**2. babel-cli** : When you are developing, you should install babel-cli on your computer by yarn or npm **Globally**.  
It will provide you command like "babel" & "babel-node" to compile files.

**3. babel-polyfill** : You should add it to your project dependency for your client. They will need it to use command "node" to run files that you compiled by babel-cli.

More detail in chiness is [here](https://code.kpman.cc/2016/09/13/babel-%E7%9B%B8%E9%97%9C%E5%90%8D%E8%A9%9E%E7%B0%A1%E4%BB%8B/).

# Installation

The first you should do is put **.babelrc** file to your project directory, then you follow the step below.

### For Developer :
Just like I metioned up there, you should install **babel-cli** on your computer by yarn or npm **Globally**.
```=bash
yarn global add babel-cli
// or
npm install babel-cli -g
```
Also, you will need **babel-preset** for compiling.
```=bash
yarn add babel-preset-env -D
// or
npm install babel-preset-env -D
```

### For Client :

You should add **babel-polyfill** as dependency for your client.
```=bash
yarn add babel-polyfill
// or
npm install babel-polyfill --save
```

# Usage

## babel-cli

If you want compile file by babel, you should use something like
```=bash
babel src/index.js -d build
```
After this, your client only need babel-polyfill and node to run the file you just compiled.

Also you can directly run js file with babel.
```=bash
babel-node src/index.js
```

## Production
If you follow the step of Installation correctly, then after cloning your project, your client only need to use these command
```=bash
yarn install --prod
// or
npm install -P

node build/index.js
```