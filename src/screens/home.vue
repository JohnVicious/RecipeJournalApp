<template>
	<nb-container>
		<image-background :source="launchScreenBg" class="imageContainer">
		  <view class="logoContainer" :style="stylesObj.logoContainerStyle">
			<image-background
			  :source="launchscreenLogo"
			  class="logo"
			  :style="stylesObj.logoStyle"
			/>
		  </view>
		  <view class="text-container">
			<nb-h3 :style="{ marginBottom: 8 }" class="text-color"
			  >Welcome to The Recipe Journal</nb-h3
			>
			<nb-h3 class="text-color">Store all of your favorite recipes!</nb-h3>
		  </view>
		  <view :style="{ marginBottom: 80 }">
			<nb-button
			  :style="stylesObj.btnContainer"
			  :onPress="handleLetGoBtnPress"
			>
			  <nb-text> Lets Go!</nb-text>
			</nb-button>
		  </view>
		</image-background>
	</nb-container>
</template>

<script>
import { Dimensions, Platform } from "react-native";	
import launchScreenBg from "../../assets/launchscreen-bg.png";
import launchscreenLogo from "../../assets/logo-recipe-journal.png";

export default {
	name: 'home',
	props: {
		navigation: {
			type: Object
		}
	},
	data: function(){
		return {
			launchScreenBg,
			launchscreenLogo,
			stylesObj: {
				logoContainerStyle: {
					marginTop: Dimensions.get("window").height / 8
				},
				logoStyle: {
					left: Platform.OS === "android" ? 65 : 50,
					top: Platform.OS === "android" ? 35 : 60
				},
				btnContainer: {
					backgroundColor: "#80C13A",
					alignSelf: "center"
				}
			}
		};
	},
	async created() {
				
	},
    methods: {
		handleLetGoBtnPress() {
			this.navigation.openDrawer();
		}
	}
};
</script>

<style scoped>
.imageContainer {
  flex: 1;
}
.logoContainer {
  flex: 1;
  margin-bottom: 20;
}
.logo {
  position: absolute;
  align-self: center;
  width: 280;
  height: 154;
}
.button-container {
  background-color: #80C13A;
  align-self: center;
}
.text-container {
  align-items: center;
  margin-bottom: 30;
  background-color: transparent;
}
.text-color {
  color: #374d20;
  font-weight: bold;
}
</style>