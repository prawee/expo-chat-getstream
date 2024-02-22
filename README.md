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

## Reference

<https://getstream.io/chat/react-native-chat/tutorial/?language=Expo>