# android-glassmorphismfactory
Applying Glassmorphism effect now in your Android project is no nightmare using our library GlassmorphismFactory.

Infact, now it's easy as pressing a button.

![GlassmorphismFactory Example](https://raw.githubusercontent.com/theignitedflame/android-glassmorphismfactory/main/GlassmorphismFactory_example.jpg)

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

# How to use it ?

Go to your activity ```onCreate(Bundle)``` and prepare and link your views like this :
```java
import com.flame.ui.GlassmorphismFactory;
import com.flame.ui.GlassmorphismFactory.BlurListener;
import com.flame.ui.GlassmorphismFactory.GlassmorphismDrawable;

...
public class MyActivity extends Activity {

...
@Override
public void onCreate(Bundle bundle) {
    super.onCreate(bundle);
    ...

    /* Link our Activity to GlassmorphismFactory */
     GlassmorphismFactory.setActivity(this);
    /* Provide a default blur radius (not necessary, default blur value automatically setted to 25) */
     GlassmorphismFactory.setDefaultBlurRadius(int radius); // blur radius value confined between 0 and 25
    /* Link our view(s) to GlassmorphismFactory and a BlurListener */
     GlassmorphismFactory.setBlurListener(View view, BlurListener listener);

    /* Example :
    *  GlassmorphismFactory.setBlurListener(mylayout, new BlurListener() {
        @Override
        public void whenBlurIsReady(View view, GlassmorphismDrawable drawable) {
            // do whatever you want with drawable (extends GradientDrawable) (a mix between GradientDrawable and BitmapDrawable)
            // simple use : view.setBackground(drawable);
            // another simple use : view.setForeground(drawable);
            ...
        }
        @Override
        public void whenResetBlur(View view) {
        // Called when blur generator wants to clear the previous GlassmorphismDrawable you setted (as a background/foreground for example) to avoid blur duplications
        // Useful when you include the view in its generated blur to avoid duplications
        // Not needed when you dont include it
        // simple use : view.setBackgroundColor(Color.TRANSPARENT);
        // another simple use : view.setForeground(new ColorDrawable(Color.TRANSPARENT));
        ....
        }
    });
    */

     /* If you want to set a specified blur value to a view */
     GlassmorphismFactory.setBlurRadius(View view, int radius); // blur radius value confined between 0 and 25

     /* If you want to include the setted|linked view in its generated Glassmorphism blur */
     GlassmorphismFactory.setViewIncludedInBlur(View view, boolean included);

     /* And then we start generating blur */
     GlassmorphismFactory.startGeneratingBlur();

     /* You can stop it later if you want, and also you can check if the generator is running or not */
     // if (GlassmorphismFactory.isGeneratingBlur()) GlassmorphismFactory.stopGeneratingBlur();

     ....
    }
...
```


# Methods Documentation

- They are all static methods, call them using GlassmorphismFactory.the_method_you_wanna_call.


# public static void setActivity(Activity act)
- This method links a activity to GlassmorphismFactory (actually the window of it).

    
# public static void setWindow(Window window)
- This method links a window to GlassmorphismFactory.

    
# public static void setBlurListener(View view, BlurListener lis)
- This method links a blur listener to a view.
- It also link the view to the GlassmorphismFactory for preparation.
- This method should always be called before startGeneratingBlur method or nothing is gonna start.
    
# public static void setBlurRadius(View view, int radius)
- This method specifies a blur radius value to a view.
- Blur radius is always confined between 0 and 25.
   
    
# public static void setViewIncludedInBlur(View view, boolean included)
- Include the linked view into its generated Glassmorphism blur.
- Useful when applying the GlassmorphismDrawable as a foreground.
- You must override whenResetBlur(View view) listener method in your BlurListener and clear your previous setted GlassmorphismDrawable to avoid blur duplication.
    
# public static void setDefaultBlurRadius(int radius)
- This method adds a general blur radius to all non specified views.
- This method doesn't effect the setBlurRadius method (When you apply a specified blur value to a view, the generator ignores the default value).
- This method must be called before startGeneratingBlur.
-  Blur radius is always confined between 0 and 25.
    
    
    
# public static void startGeneratingBlur()
- And all the magic happens here :) .
- We must trigger this method in order to apply the Glassmorphism effect to our views.
- All the generated bitmaps here takes the size of its views so I think its memory safe if you're not applying it to big/a lot of views.

# public static void stopGeneratingBlur()
This method stops generating Glassmorphism effect
   
# public static boolean isBlurGeneratingStarted()
This method checks if blur generating is started.
