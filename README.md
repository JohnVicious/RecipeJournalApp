# RecipeJournalApp
 An app made for my personal favorite recipes.
 
## Getting Started

 The RecipeJournalApp is an android application made using the Vue Native framework. Through EXPO, it can be ran and compiled into an android APK and installed to phones or ran through an android emulator.
 
 ### Requirements
 
 In order to run the app and compile it, the following will be needed:
 
* [NPM](https://nodejs.org/en/) - Package manager for JS libraries

### Prerequisites

The RecipeJournalAPI needs to be implemented in order for the application to pull needed data.

* [RecipeJournalAPI](https://github.com/JohnVicious/RecipeJournalApp)

### Installing

After cloning the repository and implementing the RecipeJournalAPI:

Install node packages
```
npm install
```

Once node has completed, you can run the app on an android emulator.
```
npm run android
```

To compile the application, use expo:
```
expo build:android
```

## Built With

* [Vue-Native](https://vue-native.io/) - Javascript framework
* [Expo](https://docs.expo.io/) - Deployment framework

## Authors

* **John Klein** - https://github.com/JohnVicious - https://www.johnklein.dev

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

## Future Plans

Need to implement the following:

* Local system storage
* Favorites
* Adding recipes from application