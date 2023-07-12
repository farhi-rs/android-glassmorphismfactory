# android-glassmorphismfactory
Applying Glassmorphism effect now in your Android project is no nightmare using our library GlassmorphismFactory.

Infact, now it's easy as pressing a button.

Just link your [Activity](https://developer.android.com/reference/android/app/Activity) or your [Window](https://developer.android.com/reference/android/view/Window) and your [View](https://developer.android.com/reference/android/view/View)s to GlassmorphismFactory, use setBlurRadius(View view, int radius) or setDefaultBlurRadius(int radius), link GlassmorphismFactory.BlurListener to your [View](https://developer.android.com/reference/android/view/View) | [View](https://developer.android.com/reference/android/view/View)s using setBlurListener(View view, BlurListener listener), call startGeneratingBlur() and tada 🎉 you have successfully and easily applied Glassmorphism effect to your [View](https://developer.android.com/reference/android/view/View), how easy is that 😀.

# How our library works

Our library uses [Android](https://github.com/android)'s [RenderScript Intrinsics Replacement Toolkit](https://github.com/android/renderscript-intrinsics-replacement-toolkit) library to blur the captured [View](https://developer.android.com/reference/android/view/View) background [Bitmap](https://developer.android.com/reference/android/graphics/Bitmap) and give it to the user/developer through GlassmorphismFactory.BlurListener as a GlassmorphismDrawable and let the user/developer do whatever he want with it (set it as a background/foreground/draw it/set it for other views/apply color filter to it/apply rounded corners to it/ etc...).

Thanks to [Android](https://github.com/android) for providing this incredible library even though its in beta version 😶.

# Adding our library to your project

To add GlassmorphismFactory library to your android project you can do the following :

Using gradle :

- Add it in your root build.gradle at the end of repositories:
```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
```
- Step 2. Add the dependency
```
	dependencies {
	        implementation 'com.github.theignitedflame:android-glassmorphismfactory:v1.0.0-beta'
	}
```

Or download the jar file using this link : https://github.com/theignitedflame/android-glassmorphismfactory/releases/download/v1.0.0-beta/android-glassmorphismfactory-v1.0.0-beta.jar

# Methods Documentation

