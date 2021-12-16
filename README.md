# tabs-navigation-examples
Referencia: https://www.luiztools.com.br/post/tutorial-crud-em-app-android-e-ios-com-react-native/

1. criar uma pasta crud
2. no terminal, 
> expo init crudReact
> cd crudReact
3. no terminal ainda, executar o comando:
> npm install @react-navigation/native
> expo install react-native-gesture-handler react-native-reanimated react-native-screens react-native-safe-area-context @react-native-community/masked-view
> npm install @react-navigation/bottom-tabs


Em seguida, criar três arquivos em branco.

AppForm.js
AppList.js
AppTab.js


AppForm.js

import { StatusBar } from 'expo-status-bar';
import React from 'react';
import { StyleSheet, Text, View } from 'react-native';
 
export default function AppForm() {
  return (
    <View style={styles.container}>
      <Text>Form!</Text>
      <StatusBar style="light" />
    </View>
  );
}
 
const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#D93600',
    alignItems: 'center',
    justifyContent: 'center',
  },


AppList

import { StatusBar } from "expo-status-bar";
import React from "react";
import { StyleSheet, Text, View } from "react-native";

export default function AppList() {
  return (
    <View style={styles.container}>
      <Text>List!</Text>
      <StatusBar style="light" />
    </View>
  );
}

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: "#D93600",
    alignItems: "center",
    justifyContent: "center",
  },
});



AppTab

import React from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createBottomTabNavigator } from '@react-navigation/bottom-tabs';
 
import AppList from './AppList';
import AppForm from './AppForm';
 
const { Navigator, Screen } = createBottomTabNavigator();
 
function AppTab() {
    return (
        <NavigationContainer>
            <Navigator
                screenOptions={{
                    tabBarActiveTintColor: "#32264d",
                    tabBarInactiveTintColor: "#c1bccc",
                    tabBarActiveBackgroundColor: "#ebebf5",
                    tabBarInactiveBackgroundColor: "#fafafc",
                    tabBarLabelStyle: {
                        fontSize: 13,
                        position: 'absolute',
                        top: 15,
                        bottom: 0,
                        left: 0,
                        right: 0
                    },
                    tabBarIconStyle: { display: "none" }
                }}
            >
                <Screen name="AppList" component={AppList} />
                <Screen name="AppForm" component={AppForm} />
            </Navigator>
        </NavigationContainer>
    );
}
 
export default AppTab;


Atualize o arquivo App.js

import { StatusBar } from 'expo-status-bar';
import React from 'react';
 
import AppTab from './AppTab';
 
export default function App() {
  return (
    <>
      <AppTab />
      <StatusBar style="light" />
    </>
  );
}
