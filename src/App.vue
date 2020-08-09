<template>
  <root>
	<status-bar :backgroundColor="'#80C13A'" :barStyle="'light-content'"></status-bar>
    <app-navigation></app-navigation>
  </root>
</template>

<script>
import {
  createAppContainer,
  createStackNavigator,
  createDrawerNavigator
} from "vue-native-router";
import { Root } from "native-base";
import HomeScreen from "./screens/home.vue";
import RecipesScreen from "./screens/recipes.vue";
import RecipeScreen from "./screens/recipe.vue";
import FavoritesScreen from "./screens/favorites.vue";
import AddRecipeScreen from "./screens/addRecipe.vue";
import SideBarScreen from "./screens/sidebar.vue";

const Drawer = createDrawerNavigator(
	{
		Home: { screen: HomeScreen },
		Recipes: { screen: RecipesScreen },
		Favorites: { screen: FavoritesScreen },
		AddRecipe: { screen: AddRecipeScreen }
	},
	{
		initialRouteName: "Home",
		contentOptions: {
			activeTintColor: "#e91e63"
		},
		contentComponent: SideBarScreen
	}
);

const AppNavigation = createAppContainer(
	createStackNavigator(
		{
			Drawer: { screen: Drawer },
			Recipe: { screen: RecipeScreen },			
			AddRecipe: { screen: AddRecipeScreen }
		},
		{
			initialRouteName: "Drawer",
			headerMode: "none"
		}
	)
);

export default {
  components: { Root, AppNavigation }
};
</script>
