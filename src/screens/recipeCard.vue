<template>
	<nb-content padder class="bottomMargin" :style="stylesObj.cardContainer">
		<nb-card>
			<nb-card-item>
				<nb-left>
					<nb-body>
						<nb-text>{{recipeData.Title}}</nb-text>
						<nb-text note>{{recipeData.SubTitle}}</nb-text>
					</nb-body>
				</nb-left>
			</nb-card-item>

			<nb-card-item cardBody>
				<image
					:source="{uri: getCardImage(recipeData.Image)}"
					class="card-item-image"
					:style="stylesObj.cardItemImage"
				/>
			</nb-card-item>

			<nb-card-item>
				<nb-left>
					<nb-button
					  :style="stylesObj.btnContainer"
					  :key="routeInfo.route"
					  button
					  :onPress="() => handler.props.navigation.navigate(routeInfo.route,{data:recipeData})"
					>
					  <nb-text>View Recipe</nb-text>
					</nb-button>
				</nb-left>
				<nb-body/>
				<nb-right/>						
			</nb-card-item>
		</nb-card>
	</nb-content>
</template>

<script>
	export default {
		name: 'recipeCard',
		props: ["recipeData","handler"],
		data: function(){
			return {
				routeInfo: {
					route: "Recipe"
				},
				stylesObj: {
					cardItemImage: {
						resizeMode: "cover"
					},			
					btnContainer: {
						backgroundColor: "#80C13A",
						alignSelf: "center"
					},			
					cardContainer: {
						backgroundColor: "#fff"
					}
				}
			}
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
  flex: 1;
  height: 200;
}	
.bottomMargin{
	margin-bottom: 20px;
}
</style>