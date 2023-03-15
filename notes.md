# Create an Uber Clone
 
 npx create-expo-app Uber_Clone

 ## Setup Redux

npm install @reduxjs/toolkit 
npm add react-redux
import {Provider} from "react-redux";

A provider is a wrapper added to app.js 

enclose your app with 
<Provider>
 <View style={styles.container}>
      <Text>Uber !</Text>
      <StatusBar style="auto" />
    </View>
<Provider/>


This brings an error because when using redux you must have a store.js 
It allows pushing and pulling data within the app (REdux works kidna like context api)

create a new store.js file to add config
in store.js add
{
 import { configureStore } from '@reduxjs/toolkit'

export const store = configureStore({
  reducer: {},
})
}
### create a Slice

Crete a folder slices and in it add navSlice.js
For more details check out react redux documentation ie https://redux-toolkit.js.org/tutorials/quick-start

create initialState and add required parameters ie
{
    import {createSlice} from "@reduxjs/toolkit"


// This is the initialState of the app data layer
const initialState = {
    origin: null,
    destination: null,
    travelTimeInformation: null, 
}

export const navSlice = createSlice({
    name: 'nav',
    initialState,
    reducer: {
        setOrigin: (state, action)=>{
            state.origin = action.payload;
        },
        setDestination: (state, action)=>{
            state.destination = action.payload;
        },
        setTravelTimeInformation: (state, action)=>{
            state.travelTimeInformation = action.payload;
        },
    },
});

export const {setOrigin, setDestination, setTravelTimeInformation} = navSlice.actions;
/// This pushes data to datalayer

///USe selectors to grab info from data layer
/// Use one selector for each of the params of initialState

export const selectOrigin = (state) => state.nav.origin;
export const selectDestination = (state) => state.nav.destination;
export const selectTravelTimeInformation = (state) => state.nav.travelTimeInformation;

export default navSlice.reducer;
}

### Add slice to store 

{

    import { configureStore } from '@reduxjs/toolkit'
import navReducer from "./slices/navSlice"

export const store = configureStore({
  reducer: {
    nav: navReducer
  },
})

}

add store to provider and import to app.js

## Creating Homepage

Create a screens folder and a HomeScreen Component 

 ### adding tailwind css to react native
 in terminal run: npm i tailwind-react-native-classnames

 in the component to use tailwind remember to import 
 import tw from 'tailwind-react-native-classnames';
 ### using react native elements 

 Go to https://reactnativeelements.com/docs/installation
 Install stable version : npm install @rneui/themed @rneui/base Or  npm install react-native-elements
Add vector icons: npm install react-native-vector-icons
Add safe area context: npm install react-native-safe-area-context
To use the icons go to

To auto import use ctrl+ spacebar

## Add React navigation
To use react navigation 6 add the following

npm install @react-navigation/native
npx expo install react-native-screens react-native-safe-area-context
npm install @react-navigation/native-stack



### Adding code to github repository
 In settings Git:Enabled
 git -version
 git init
 git add .
 git commit -m "My first Commit"
 git branch -M master
 git remote add Repository url
 git push -u origin master

 ### making Commits
 -> git add .
 -> git commit -m "Write relevant message"
 -> git push origin master


 -> git branch branchName      Create a new branch
 -> git checkout branchName    Switch to the branch
 -> git branch -r              Show remote Branches
 -> git branch --show-current   Show current Branch

Incase of error I dont know who you are:
 git config -global user.name "Your Name"
 git config -global user.email "Your Email"

## Google Places Api

Install Google places autocomplete: npm install react-native-google-places-autocomplete --save
After installation go to google cloud platform

To debug node modules
first confirm latest env: npm install / yarn install
Clear Cache: 
incase of the red screen of death(rsd): rm -rf node-modules
This clears all the node modules in your prog
