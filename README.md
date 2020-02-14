[中文](https://github.com/Cocos-BCX/cocos-dice-sample/blob/master/README_cn.md)  

## cocos-dice
A Fully-Functional Dice DApp Game for the Cocos-BCX Platform

## Prerequisites

* Node.js 8.9+
* yarn

### Wallet  

* [CocosPay Chrome Extension](https://chrome.google.com/webstore/detail/cocospay/ffbhaeoepdfapfjhcihbbhlaigejfack)
* Alternatively [CocosPay from Source](https://github.com/Cocos-BCX/CocosPay)  

Or, alternatively (for Chrome & non-Chrome), install CocosDesktop Wallet  

[CocosDesktop for Mac](https://cocosbcx.oss-cn-beijing.aliyuncs.com/CocosDesktop.dmg)  
[CocosDesktop for Windows](https://cocosbcx.oss-cn-beijing.aliyuncs.com/CocosDesktop.exe)  

### Login  
Open wallet, set to English, set to TESTNET, then sign in or sign up for an account.


## Build and Run

```sh
yarn install
yarn build
yarn serve
```

## Open App in Browser

App should be available at: http://localhost:8080/

Your first interaction will show a dialogue, check the checkbox bottom left and the press ok (dialogue may be in chinese).

``` test
Notice: 
1. If you are using Google Chrome extension wallet, do open the link with Chrome;
2. Make sure you've installed wallet correctly and logged in
```

Output should be something like:

![avatar](https://github.com/Cocos-BCX/cocos-dice-sample/blob/master/run_serve.png)
