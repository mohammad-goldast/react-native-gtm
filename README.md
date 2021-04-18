# react-native-gtm
React Native wrapper package for using native Google tag manager libraries on iOS and Android.

## Installation


1. Install `react-native-gtm` by  `this repo`.

    ```
    npm install https://github.com/mohammad-goldast/react-native-gtm/tree/master
    ```

2. extra step for IOS native project: 

- Open iOS project by Xcode, click `project name` node , then find `Build Phases` tab at right side windows , expand `Link Binary With Libraries` section , add below libraries:
    
    ```
    CoreData.framework
    SystemConfiguration.framework
    libz.tbd
    libsqlite3.0.tbd
    AdSupport.framework
    ```

## How to use

#### openContainerWithId(containerId)
Import the libaries and call `openContainerWithId` to create singleton instance.
```js
import GoogleTagManager from 'react-native-gtm';
```

```js
const InitGTM = () => {
    GoogleTagManager.openContainerWithId("GTM-XXXX")
      .then(function(){
          //open container success
      })
}
    
```

1. If first key **is** `event` , the `push` will fire a event with others keyPairs to `datalayer`. 

```
GoogleTagManager.push({
   event:"openScreen",
   screenName:"HomeScreen",
   appName:"HelloApp"
});
```
    
2. If first key **not** `event` , the `push` will send keyPairs value to `datalayer`. 

```
GoogleTagManager.push({
   sku:"some sku",
   productName:"some product name",
   price:123,
   ...
});
```

3. let value is `null` to clean the datalayer data. 

```
GoogleTagManager.push({
   sku:null,
   productName:null,
   price:null,
   ...
});
```

 
## Reference
1. [Google Tag Manager - iOS](https://developers.google.com/tag-manager/ios/v3/)
2. [Google Tag Manager - Android](https://developers.google.com/tag-manager/android/v4/#getting-started)
3. [Universal Analytics Tags - iOS](https://developers.google.com/tag-manager/ios/v3/ua)
4. [Universal Analytics Tags - Android](https://developers.google.com/tag-manager/android/v4/ua)

