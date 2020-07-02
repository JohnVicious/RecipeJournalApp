<template>
	<nb-container :style="{ backgroundColor: '#fff' }">
		<nb-header :androidStatusBarColor="'#80C13A'" :iosBarStyle="'light-content'" :style="{ backgroundColor: '#80C13A' }">
			<nb-left>
				<nb-button transparent :onPress="() => this.props.navigation.goBack()">
					<nb-icon name="arrow-back" />
				</nb-button>
			</nb-left>
			<nb-body>
				<nb-title>Recipe</nb-title>
			</nb-body>
			<nb-right />
		</nb-header>
		<nb-content padder>
			<nb-card>
				<nb-card-item bordered>
					<nb-left>
						<nb-body>
							<nb-text>{{ recipeData['Title'] }}</nb-text>
							<nb-text note>{{ recipeData['Title'] }}</nb-text>
						</nb-body>
					</nb-left>
				</nb-card-item>

				<nb-card-item>
					<nb-body>
						<image
							:source="{uri: getCardImage(recipeData.Image)}"
							class="card-item-image"
							:style="stylesObj.cardItemImage"
						/>
					</nb-body>
				</nb-card-item >
				
				<nb-list-item itemDivider v-if="recipeData.Story != ''">
					<nb-text>{{ recipeData.Story }}</nb-text>
				</nb-list-item>
				
				<nb-card-item cardBody>
					<nb-body>
						<nb-text :style="stylesObj.mainText" v-if="recipeData.Servings > 0">						
							Servings : {{ recipeData.Servings }}
						</nb-text>
						<nb-text :style="stylesObj.mainText" v-if="recipeData.Serves > 0">	
							Serves : {{ recipeData.Serves }}
						</nb-text>
						<nb-text :style="stylesObj.mainText" v-if="recipeData.Serves != ''">	
							Prep Time : {{ recipeData.PrepTime }}
						</nb-text>
						<nb-text :style="stylesObj.mainText" v-if="recipeData.CookTime != ''">	
							Cook Time : {{ recipeData.CookTime }}
						</nb-text>
						<nb-text :style="stylesObj.mainText" v-if="recipeData.Calories > 0">	
							Calories : {{ recipeData.Calories }}
						</nb-text>
						<nb-text :style="stylesObj.spacerText"/>							
					</nb-body>					
				</nb-card-item>
				
				<nb-list-item itemDivider>
					<nb-text>Ingredients</nb-text>
				</nb-list-item>
				<nb-list-item v-for="ingredient in recipeData.Ingredients">
					<nb-text>{{ingredient.measurement}} - {{ingredient.item}}</nb-text>
				</nb-list-item>
				
				<nb-list-item itemDivider>
					<nb-text>Instructions</nb-text>
				</nb-list-item>
				<nb-list-item v-for="instruction in recipeData.Instructions">
					<nb-text>{{instruction.number}} - {{instruction.step}}</nb-text>
				</nb-list-item>
				
				<nb-list-item itemDivider v-if="recipeData.Notes.length > 0">
					<nb-text>Notes</nb-text>
				</nb-list-item>
				<nb-list-item v-if="recipeData.Notes.length > 0" v-for="note in recipeData.Notes">
					<nb-text>• {{note.item}}</nb-text>
				</nb-list-item>
				
			</nb-card>
		</nb-content>
	</nb-container>
</template>

<script>
import { Dimensions } from "react-native";
import logo from "../../assets/logo.png";

const deviceWidth = Dimensions.get("window").width;

export default {
	props : ["navigation"],
	data() {
		return {
			logo,
			recipeData: this.navigation.getParam("data"),
			stylesObj: {
				cardItemImage: {
					resizeMode: "cover",
					width: deviceWidth / 1.18
				},
				mainText: {
					marginBottom: -30,
					fontSize: 17
				},
				spacerText: {
					marginBottom: 10
				}
			}
		};
	},
	methods: {
		getCardImage(imageSource){
			var img = imageSource;
			var imgRequire = 'https://www.johnklein.dev/RecipeJournal/assets/recipeImages/'+img;
			return imgRequire;
		}
	}
};

</script>

<style scoped>
.card-item-image {
	align-self: center;
	height: 200;
	margin-vertical: 5;
}
</style>