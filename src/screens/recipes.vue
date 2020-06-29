<template>
	<nb-container>
		<nb-header :androidStatusBarColor="'#80C13A'" :iosBarStyle="'light-content'" :style="{ backgroundColor: '#80C13A' }">
			<nb-left>
				<nb-button
					transparent
					:onPress="() => this.props.navigation.openDrawer()"
				>
					<nb-icon name="menu" />
				</nb-button>
			</nb-left>
			<nb-body>
				<nb-title>Recipes</nb-title>
			</nb-body>			
			<nb-right />
		</nb-header>
		<nb-container>
			<scroll-view class="scroll-view">
				<recipeCard v-for="r in recipes" :recipeData="r" :handler="this" :key="r.ID"/>
			</scroll-view>
		</nb-container>  
	</nb-container>
</template>

<script>
import { Dimensions, Platform } from "react-native";
import axios from "axios";
import RecipeCard from './recipeCard';	
import { View, StatusBar, ViewPropTypes, SafeAreaView } from 'react-native';

export default {
	name: 'recipes',
	data: function(){
		return {
			recipes: [],
			stylesObj: {
				logoContainerStyle: {
					marginTop: Dimensions.get("window").height / 8
				},
				logoStyle: {
					left: Platform.OS === "android" ? 40 : 50,
					top: Platform.OS === "android" ? 35 : 60
				}
			}
		};
	},
	async created() {
		axios
			.get(
				"https://www.johnklein.dev/RecipeJournal/recipeJournalAPI.php"
			)
			.then(
				response => (
					(this.recipes = response.data)
				)
			);
			
		
		this.loading = false;			
	},
	components: {RecipeCard}
};
</script>

<style scoped>
.scroll-view {
	padding-top: 20px;
	padding-bottom: 30px;
	height: 100%;	
}
</style>