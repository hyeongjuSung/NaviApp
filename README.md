NaviApp 201740220 성형주
=============
NaviApp 프로젝트
-------------
## 05.28
> NaviApp 프로젝트
### NaviApp 프로젝트 생성
```javascript
- reatc-native init NaviApp
※ 프로젝트 폴더를 미리 만들고 그 안에서 명령을 수행하면 프로젝트 폴더가 미리 생성되므로 주의
```
### 프로젝트가 정상적으로 생성되었는지 확인
```
- npm run android
```
### react-navigation V5 설치
```
참고: https://reactnavigation.org/docs/getting-started/
- npm install @react-navigation/native
- npm install react-native-reanimated react-native-gesture-handler react-native-screens react-native-safe-area-context @react-native-community/masked-view
```
### 스택 내비게이션 라이브러리 추가
```javascript
- npm install @react-navigation/stack

// 스택 내비게이션 예제
import 'react-native-gesture-handler';
import * as React from 'react';
import { View, Text } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createStackNavigator } from '@react-navigation/stack';

function HomeScreen() {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>Home Screen</Text>
    </View>
  );
}

function DetailsScreen() {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Text>Details Screen</Text>
    </View>
  );
}

const Stack = createStackNavigator();

function App() {
  return (
    <NavigationContainer>
      <Stack.Navigator>
        <Stack.Screen name="Home" component={HomeScreen} />
        <Stack.Screen name="Details" component={DetailsScreen} />
      </Stack.Navigator>
    </NavigationContainer>
  );
}

export default App;
```
### 스택 내비게이션에서의 스크린 이동
```javascript
- onPress 속성을 이용하여 버튼 클릭 시 스크린 이동

<Button
    title="Go to Details"
    onPress={() => navigation.navigate('Details')}
/>

- 여러개의 스크린을 쌓는 방법(DetailScreen)

<Button
  title="Go to Details... again"
  onPress={() => navigation.push('Details')}
/>

```
### 탭 내비게이션 라이브러리 추가
```javascript
- npm install @react-navigation/bottom-tabs

// 탭 내비게이션 예제
import 'react-native-gesture-handler';
import * as React from 'react';
import { Text, View } from 'react-native';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';

function HomeScreen() {
  return (
    <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
      <Text>Home!</Text>
    </View>
  );
}

function SettingsScreen() {
  return (
    <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
      <Text>Settings!</Text>
    </View>
  );
}

const Tab = createBottomTabNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Tab.Navigator>
        <Tab.Screen name="Home" component={HomeScreen} />
        <Tab.Screen name="Settings" component={SettingsScreen} />
      </Tab.Navigator>
    </NavigationContainer>
  );
}

```
### 드로어 내비게이션 라이브러리 추가
```javascript
- npm install @react-navigation/drawer

// 드로어 내비게이션 예제
import * as React from 'react';
import { Button, View } from 'react-native';
import { createDrawerNavigator } from '@react-navigation/drawer';
import { NavigationContainer } from '@react-navigation/native';

function HomeScreen({ navigation }) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Button
        onPress={() => navigation.navigate('Notifications')}
        title="Go to notifications"
      />
    </View>
  );
}

function NotificationsScreen({ navigation }) {
  return (
    <View style={{ flex: 1, alignItems: 'center', justifyContent: 'center' }}>
      <Button onPress={() => navigation.goBack()} title="Go back home" />
    </View>
  );
}

const Drawer = createDrawerNavigator();

export default function App() {
  return (
    <NavigationContainer>
      <Drawer.Navigator initialRouteName="Home">
        <Drawer.Screen name="Home" component={HomeScreen} />
        <Drawer.Screen name="Notifications" component={NotificationsScreen} />
      </Drawer.Navigator>
    </NavigationContainer>
  );
}
```