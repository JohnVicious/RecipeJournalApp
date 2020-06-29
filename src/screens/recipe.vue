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
							:source="cardImage"
							class="card-item-image"
							:style="stylesObj.cardItemImage"
						/>
						<nb-text>
						{{ recipeData['Body'] }}
						</nb-text>
					</nb-body>
				</nb-card-item>
			</nb-card>
		</nb-content>
	</nb-container>
</template>

<script>
import { Dimensions } from "react-native";
import logo from "../../assets/logo.png";
import cardImage from "../../assets/card-noImage.png";

const deviceWidth = Dimensions.get("window").width;

export default {
	props : ["navigation"],
	data() {
		return {
			logo,
			cardImage,
			recipeData: this.navigation.getParam("data"),
			stylesObj: {
				cardItemImage: {
					resizeMode: "cover",
					width: deviceWidth / 1.18
				}
			}
		};
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