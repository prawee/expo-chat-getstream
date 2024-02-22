# Expo with getSteam

## Initial project
```bash
expo init expo-getsteam
```

## Package and dependencies
```bash
expo install stream-chat-expo

expo install @stream-io/flat-list-mvcp @react-native-community/netinfo expo-file-system expo-image-manipulator expo-image-picker expo-media-library react-native-gesture-handler react-native-reanimated react-native-svg

expo install expo-document-picker expo-av expo-haptics expo-sharing expo-clipboard
```

## Configure
```bash
nano babel.config.js
```
```bash
module.exports = {
    ...
    plugins: [
        'react-native-reanimated/plugin',
    ]
}
```

## Register component
```bash
nano index.js
```
```bash
import 'react-native-gesture-handler'
import { AppRegistry } from 'react-native'

import App from './App'
import { name as appName } from './app.json'

AppRegistry.registerComponent(appName, () => App)
```

## Navigation Stack
```bash
npx expo install @react-navigation/native@^6.0.10 @react-navigation/stack@^6.2.1  react-native-screens@^3.13.1 react-native-safe-area-context@^4.2.5
```
```bash
npx expo prebuild || expo run:ios || expo run:android
# com.teohong.phone
# ...
# ✔ Finished prebuild
# ✔ Installed CocoaPods
npx pod-install
```

## Make Screen
- Update App.js
```bash
import React from 'react'
import { NavigationContainer } from '@react-navigation/native'
import { createStackNavigator } from '@react-navigation/stack'
import { SafeAreaView } from 'react-native-safe-area-context'
import { Text } from 'react-native'

const Stack = createStackNavigator()

const HomeScreen = () => <Text>Home Screen</Text>

const NavigationStack = () => {
  return (
    <Stack.Navigator>
      <Stack.Screen name='Home' component={HomeScreen} />
    </Stack.Navigator>
  )
}

export default () => {
  return (
    <SafeAreaView style={{ flex: 1 }}>
      <NavigationContainer>
        <NavigationStack />
      </NavigationContainer>
    </SafeAreaView>
  )
}
```

## Fix package and dependencies for Calling
```bash
npx expo install @stream-io/video-react-native-sdk @stream-io/react-native-webrtc
npx expo install react-native-incall-manager@4.1.0 @react-native-community/netinfo@9.3.9 @notifee/react-native@7.7.1
npx pod-install
```

## Permissions
### Android
- android/app/src/main/AndroidManifest.xml
```xml
<manifest ...>
  <user-feature android:name="android.hardware.camera" />
  <user-feature android:name="android.hardware.camera.autofocus" />
  <user-feature android:name="android.hardware.audio.output" />
  <user-feature android:name="android.hardware.microphone" />
  <uses-permission android:name="android.permission.CAMERA"/>
  <uses-permission android:name="android.permission.ACCESS_NETWORK_STATE"/>
  <uses-permission android:name="android.permission.CHANGE_NETWORK_STATE"/>
  ...
</manifest>
```
- android/app/build.gradle
```bash
...
android {
  ...
  compileOptions {
      sourceCompatibility JavaVersion.VERSION_1_8
      targetCompatibility JavaVersion.VERSION_11
  }
}
...
```
- android/gradle.properties
```bash
...
android.enableDexingArtifactTransform.desugaring=false
```

## Reference

<https://getstream.io/chat/react-native-chat/tutorial/?language=Expo>
<https://www.youtube.com/watch?v=b9sQ28QUGW8>
<https://getstream.io/video/sdk/reactnative/tutorial/video-calling>