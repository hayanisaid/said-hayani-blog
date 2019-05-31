---
title: "How to create a background video in React Native"
description: "In this post, we are going to create a backgroundVideo in React Native. If you have just started with React Native check out my article What you need to know to start building mobile apps with React…"
date: "2019-04-15T21:02:58.148Z"
categories: 
  - React Native
  - Technology
  - iOS
  - Mobile App Development
  - Programming

published: true
canonicalLink: https://medium.com/@saidhayani/how-to-create-a-background-video-in-react-native-cb53304ee4f6
---

![Photo by [Fatos Bytyqi](https://unsplash.com/@fatosi?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com?utm_source=medium&utm_medium=referral)](./asset-1)

![Demo: Peleton Home Screen](./asset-2.gif)

In this post, we are going to create a `**backgroundVideo**` in React Native. If you have just started with React Native check out my article [What you need to know to start building mobile apps with React Nativ](https://medium.freecodecamp.org/what-you-need-to-know-to-start-building-mobile-apps-in-react-native-dded951277b7)e.

Background video can add a nice effect to the UI of an app. They may be helpful also if you want to display, for example, ads or send a message to the user, like we’ll do here.

You will need some basic requirements. To get started, you must have the react-native environment setup. That means you have:

-   [react-native-cli](https://github.com/react-native-community/react-native-cli) installed
-   Android SDK; if you have a mac you won’t need that, just Xcode

### Getting started

First things first, let’s bootstrap a new React Native app. In my case I’m using react-native-cli. So in your terminal run:

```
react-native init myapp
```

This should install all the dependencies and packages to run your React Native app.

Next step is to run and install the app on the simulator.

For iOS:

```
react-native run-ios
```

This should open up the iOS simulator.

On Android:

```
react-native run-android 
```

You may have some trouble with Android. I recommend that you use [Genymotion](https://www.genymotion.com/) and the Android emulator or check out [this friendly guide](https://medium.com/@sunilk/react-native-development-getting-started-with-android-and-ios-ada22e3d00b1) to set up the environment.

First what we are going to do is clone the Peleton app’s home screen. We are using `[**react-native-video**](https://github.com/react-native-community/react-native-video)` for video streaming, and `[**styled-component**](https://www.styled-components.com/docs/basics#react-native)` for styling. So you have to install them:

-   Yarn:

```
yarn add react-native-video styled-components
```

-   NPM

```
npm -i react-native-video styled-components --save
```

Then you need to link react-native-video because it contains native code — and for `**styled-components**` we don’t need that. So simply run:

```
react-native link
```

You don’t have to worry about the other things, just focus on the `Video` Component. First, import Video from react-native-video and start using it!

```
import import Video from "react-native-video";
  <Video

source={require("./../assets/video1.mp4")}

style={styles.backgroundVideo}

muted={true}

repeat={true}

resizeMode={"cover"}

rate={1.0}

ignoreSilentSwitch={"obey"}

/>
```

Let’s break it down:

-   **source**: the path to the source video. You can use the URL instead:

```
source={{uri:"https://youronlineVideo.mp4"}}
```

-   **style:** the costume style we want to give to the video, and the key to making the background video
-   resizeMode: in our case it is `cover`; you can try also `contain or stretch` but this won’t give us what we want

And other props are optional.

Let’s move to the important part: placing the video in the background position. Let’s define the styles.

```
// We use StyleSheet from react-native so don't forget to import it

//import {StyleSheet} from "react-native";
const { height } = Dimensions.get("window");

const styles = StyleSheet.create({

backgroundVideo: {

height: height,

position: "absolute",

top: 0,

left: 0,

alignItems: "stretch",

bottom: 0,

right: 0

}

});
```

What did we do here?

We gave the video a `position :absolute` and we give it the window `height` of the device. We used the `Dimensions` from React Native to ensure that the video is taking up the whole hight — `top:0, left:0,bottom:0,right:0` — so that the video takes up all the space!

The entire code:

Embed placeholder 0.676017116272402

![](./asset-3.gif)

Also, you can make this component reusable by doing the following:

```
<View>
<Video

source={require("./../assets/video1.mp4")}

style={styles.backgroundVideo}

muted={true}

repeat={true}

resizeMode={"cover"}

rate={1.0}

ignoreSilentSwitch={"obey"}

/>

{this.props.children}
</View>
```

And you can use it with other components:

Embed placeholder 0.8391099853248702

That’s pretty much it. Thank you for reading!

![Photo by [David Boca](https://unsplash.com/photos/wQZSl60DGDM?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/search/photos/app?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText)](./asset-4.jpeg)

#### Learn more about React Native:

-   [What you need to know to start building mobile apps in React Native](https://medium.freecodecamp.org/what-you-need-to-know-to-start-building-mobile-apps-in-react-native-dded951277b7)
-   [Styling in React Native](https://blog.bitsrc.io/styling-in-react-native-c48caddfbe47)

#### Other posts:

-   [JavaScript ES6, write Less — Do more](https://medium.freecodecamp.org/write-less-do-more-with-javascript-es6-5fd4a8e50ee2)
-   [How to use routing in Vue.js to create a better user experience](https://medium.freecodecamp.org/how-to-use-routing-in-vue-js-to-create-a-better-user-experience-98d225bbcdd9)
-   [Here are the most popular ways to make an HTTP request in JavaScript](https://medium.freecodecamp.org/here-is-the-most-popular-ways-to-make-an-http-request-in-javascript-954ce8c95aaa)

> You can find me [on Twitter](https://twitter.com/SaidHYN) 🐦

#### Subscribe to my Mailing list to stay tuned for upcoming articles!

<Embed src="https://upscri.be/ddda72?as_embed=true" height={350} width={700} />