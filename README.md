# Ex.No: 06 Develop a application to add animations to ImageView,Move,blink,fade,clockwise,zoom,slide operations are perform in android studio.


## AIM:

To develop a application to add animation to imageview,move,blink,fade,clockwise,zoom,slide operation using Android Studio.

## EQUIPMENTS REQUIRED:

Android Studio(Latest Version)

## ALGORITHM:
Step  1.Open Android Studio and create a new project.

Step 2.Design the layout using XML with an ImageView.

Step 3.Add an image to the drawable folder.

Step 4.Create animation effects using Java code.

Step 5.Implement Move, Blink, Fade, Clockwise, Zoom, and Slide animations.

Step 6.Apply the animations to the ImageView.

Step 7.Run the application and observe the animation effects.


## PROGRAM:
```
/*
Program to display animation operation”.
Developed by: Ragul D
Registeration Number : 212225230221
*/
```
**activity_main.xml**
```
<LinearLayout
    xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    android:gravity="center_horizontal"
    tools:context=".MainActivity">

    <ImageView
        android:id="@+id/imageview"
        android:layout_width="200dp"
        android:layout_height="200dp"
        android:layout_marginTop="40dp"
        android:contentDescription="@string/app_name"
        android:src="@drawable/techzone" />


    <!-- Row 1: Blink and Rotate -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal"
        android:layout_marginTop="20dp">

        <Button
            android:id="@+id/blink"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:layout_margin="8dp"
            android:text="Blink"/>

        <Button
            android:id="@+id/rotate"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:layout_margin="8dp"
            android:text="Rotate"/>

    </LinearLayout>

    <!-- Row 2: Fade and Move -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/fade"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:layout_margin="8dp"
            android:text="Fade"/>

        <Button
            android:id="@+id/move"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:layout_margin="8dp"
            android:text="Move"/>

    </LinearLayout>

    <!-- Row 3: Slide and Zoom -->
    <LinearLayout
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:orientation="horizontal">

        <Button
            android:id="@+id/slide"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:layout_margin="8dp"
            android:text="Slide"/>

        <Button
            android:id="@+id/zoom"
            android:layout_width="0dp"
            android:layout_height="wrap_content"
            android:layout_weight="1"
            android:layout_margin="8dp"
            android:text="Zoom"/>

    </LinearLayout>


    <!--To stop the animation of the image-->
    <Button
        android:id="@+id/stop"
        android:layout_width="match_parent"
        android:layout_height="83dp"
        android:layout_marginLeft="30dp"
        android:layout_marginTop="30dp"
        android:layout_marginRight="30dp"
        android:text="@string/stop_animation" />

</LinearLayout>
```

**MainActivity.java**
```
package com.example.animation;

import android.os.Bundle;
import android.view.View;
import android.view.animation.Animation;
import android.view.animation.AnimationUtils;
import android.widget.Button;
import android.widget.ImageView;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    // Declare variables for ImageView and Buttons
    private ImageView imageView;
    private Button blink , fade , move , rotate , slide , zoom;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Initialize ImageView and Buttons using their IDs
        imageView = findViewById(R.id.imageview);
        blink = findViewById(R.id.blink);
        rotate = findViewById(R.id.rotate);
        fade = findViewById(R.id.fade);
        move = findViewById(R.id.move);
        slide = findViewById(R.id.slide);
        zoom = findViewById(R.id.zoom);
        View stop = findViewById(R.id.stop);

        // Set up click listeners for each button to start corresponding animations
        createAnimation(blink, R.anim.blink);
        createAnimation(rotate, R.anim.rotate);
        createAnimation(fade, R.anim.fade);
        createAnimation(move, R.anim.move);
        createAnimation(slide, R.anim.slide);
        createAnimation(zoom, R.anim.zoom);

        // Set up click listener for stop button to clear any ongoing animation
        stop.setOnClickListener(v -> imageView.clearAnimation());
    }

    // Function to set up an animation for a given view and animation resource ID
    private void createAnimation(View view, int animResId) {
        view.setOnClickListener(v -> {
            // Load the animation from the specified resource ID
            Animation animation = AnimationUtils.loadAnimation(MainActivity.this, animResId);
            // Start the animation on the ImageView
            imageView.startAnimation(animation);
        });
    }
}
```
**Blink.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android">
    <alpha android:fromAlpha="0.0"
        android:toAlpha="1.0"
        android:interpolator="@android:anim/accelerate_interpolator"
        android:duration="500"
        android:repeatMode="reverse"
        android:repeatCount="infinite"/>
</set>
```
**Fade.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/accelerate_interpolator">

    <!-- duration is the time for which animation will work-->
    <alpha
        android:duration="1000"
        android:fromAlpha="0"
        android:toAlpha="1" />

    <alpha
        android:duration="1000"
        android:fromAlpha="1"
        android:startOffset="2000"
        android:toAlpha="0" />

</set>
```
**Move.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android"
    android:interpolator="@android:anim/linear_interpolator"
    android:fillAfter="true">

    <translate
        android:fromXDelta="0%p"
        android:toXDelta="75%p"
        android:duration="700" />
</set>
```
**Slide.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >
    <scale
        android:duration="500"
        android:fromXScale="1.0"
        android:fromYScale="1.0"
        android:interpolator="@android:anim/linear_interpolator"
        android:toXScale="1.0"
        android:toYScale="0.0" />
</set>
```
**Rotate.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<set
    xmlns:android="http://schemas.android.com/apk/res/android">
    <rotate
        android:duration="6000"
        android:fromDegrees="0"
        android:pivotX="50%"
        android:pivotY="50%"
        android:toDegrees="360" />

    <rotate
        android:duration="6000"
        android:fromDegrees="360"
        android:pivotX="50%"
        android:pivotY="50%"
        android:startOffset="5000"
        android:toDegrees="0" />

</set>
```
**zoom.xml**
```
<?xml version="1.0" encoding="utf-8"?>
<set xmlns:android="http://schemas.android.com/apk/res/android"
    android:fillAfter="true" >

    <scale
        android:interpolator="@android:anim/linear_interpolator"
        android:duration = "1000"
        android:fromXScale = "1"
        android:fromYScale = "1"
        android:pivotX = "50%"
        android:pivotY = "50%"
        android:toXScale = "2"
        android:toYScale = "2"/>
</set>
```

## OUTPUT
![alt text](<Screenshot 2026-11-24 094721.png>)

![alt text](<Screenshot 2026-11-24 094741.png>)

**Blink**
![alt text](<Screenshot 2026-11-24 095718.png>)

**Fade**
![alt text](<Screenshot 2026-11-24 095309.png>)

**Move**
![alt text](<Screenshot 2026-11-24 095155.png>)

**Slide**
![alt text](<Screenshot 2026-11-24 094919.png>)

**Rotate**
![alt text](<Screenshot 2026-11-24 094842-1.png>)

**Zoom**
![alt text](<Screenshot 2026-11-24 094948.png>)

## RESULT
Thus, ImageView animations such as Blink, Fade, Move, Clockwise, Zoom, and Slide were successfully implemented and executed in Android Studio.