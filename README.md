# An example of using ConstraintLayout
## Barrier (Added in 1.1)
>A Barrier references multiple widgets as input, and creates a virtual guideline based on the most extreme widget on the specified side. For example, a left barrier will align to the left of all the referenced views.

    <?xml version="1.0" encoding="utf-8"?>
    <android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        tools:context="uz.xsoft.constraintlayout.MainActivity">
    
        <Button
            android:id="@+id/bt1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="8dp"
            android:text="312312313213111313131"
            app:layout_constraintTop_toTopOf="parent" />
    
        <Button
            android:id="@+id/bt2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginBottom="8dp"
            android:layout_marginTop="8dp"
            android:text="125555555dd55ee3"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintTop_toBottomOf="@+id/bt1" />
    
        <android.support.constraint.Barrier
            android:id="@+id/barrier"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            app:barrierDirection="right"
            app:constraint_referenced_ids="bt1,bt2" />
    
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:background="#ff0000"
            app:layout_constraintLeft_toRightOf="@id/barrier" />
    
    </android.support.constraint.ConstraintLayout>
    

##Circular positioning (Added in 1.1)

>You can constrain a widget center relative to another widget center, at an angle and a distance. This allows you to position a widget on a circle. The following attributes can be used:

* layout_constraintCircle : references another widget id
* layout_constraintCircleRadius : the distance to the other widget center
* layout_constraintCircleAngle : which angle the widget should be at (in degrees, from 0 to 360)

    <?xml version="1.0" encoding="utf-8"?>
    <android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <Button
            android:id="@+id/center"
            android:layout_width="50dp"
            android:layout_height="50dp"
            android:background="@drawable/background_circle"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent" />
    
    
        <Button
            style="@style/CirlceStyle"
            app:layout_constraintCircle="@id/center"
            app:layout_constraintCircleAngle="0"
            app:layout_constraintCircleRadius="150dp" />
    
        <Button
            style="@style/CirlceStyle"
            app:layout_constraintCircle="@id/center"
            app:layout_constraintCircleAngle="60"
            app:layout_constraintCircleRadius="150dp" />
    
        <Button
            style="@style/CirlceStyle"
            app:layout_constraintCircle="@id/center"
            app:layout_constraintCircleAngle="120"
            app:layout_constraintCircleRadius="150dp" />
    
    
        <Button
            style="@style/CirlceStyle"
            app:layout_constraintCircle="@id/center"
            app:layout_constraintCircleAngle="180"
            app:layout_constraintCircleRadius="150dp" />
    
        <Button
            style="@style/CirlceStyle"
            app:layout_constraintCircle="@id/center"
            app:layout_constraintCircleAngle="240"
            app:layout_constraintCircleRadius="150dp" />
    
        <Button
            style="@style/CirlceStyle"
            app:layout_constraintCircle="@id/center"
            app:layout_constraintCircleAngle="300"
            app:layout_constraintCircleRadius="150dp" />
    </android.support.constraint.ConstraintLayout>
    
    
##Group (Added in 1.1)

>This class controls the visibility of a set of referenced widgets. Widgets are referenced by being added to a comma separated list of ids.
The visibility of the group will be applied to the referenced widgets. It's a convenient way to easily hide/show a set of widgets without having to maintain this set programmatically.

    <?xml version="1.0" encoding="utf-8"?>
    <android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <Button
            android:id="@+id/button1"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="1" />
    
        <Button
            android:id="@+id/button2"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:text="2"
            app:layout_constraintStart_toEndOf="@+id/button1" />
    
        <android.support.constraint.Group
            android:id="@+id/group"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:visibility="visible"
            app:constraint_referenced_ids="button1,button2" />
    
    
    </android.support.constraint.ConstraintLayout>
    
    
## Guideline

>Utility class representing a Guideline helper object for ConstraintLayout. Helper objects are not displayed on device (they are marked as View.GONE) and are only used for layout purposes. They only work within a ConstraintLayout.

> A Guideline can be either horizontal or vertical:
 
 * Vertical Guidelines have a width of zero and the height of their ConstraintLayout parent
 * Horizontal Guidelines have a height of zero and the width of their ConstraintLayout parent
 
 >Positioning a Guideline is possible in three different ways:
 
 * specifying a fixed distance from the left or the top of a layout (layout_constraintGuide_begin)
 * specifying a fixed distance from the right or the bottom of a layout (layout_constraintGuide_end)
 * specifying a percentage of the width or the height of a layout (layout_constraintGuide_percent)
 
 >Widgets can then be constrained to a Guideline, allowing multiple widgets to be positioned easily from one Guideline, or allowing reactive layout behavior by using percent positioning.
 
    <?xml version="1.0" encoding="utf-8"?>
    <android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <android.support.constraint.Guideline
            android:id="@+id/guideline"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:orientation="vertical"
            app:layout_constraintGuide_percent="0.26041666" />
    
        <Button
            android:id="@+id/button"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:layout_marginTop="16dp"
            android:text="Button"
            app:layout_constraintLeft_toLeftOf="@+id/guideline"
            app:layout_constraintTop_toTopOf="parent" />
    
    </android.support.constraint.ConstraintLayout>
    
    
## Placeholder (Added in 1.1)

>A Placeholder provides a virtual object which can position an existing object.
 
 >When the id of another view is set on a placeholder (using setContent()), the placeholder effectively becomes the content view. If the content view exist on the screen it is treated as gone from its original location.
 
 >The content view is positioned using the layout of the parameters of the Placeholder (the Placeholder is simply constrained in the layout like any other view).
 
    <?xml version="1.0" encoding="utf-8"?>
    <android.support.constraint.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
        xmlns:app="http://schemas.android.com/apk/res-auto"
        xmlns:tools="http://schemas.android.com/tools"
        android:layout_width="match_parent"
        android:layout_height="match_parent">
    
        <android.support.constraint.Placeholder
            android:id="@+id/place_holder"
            android:layout_width="100dp"
            android:layout_height="100dp"
            app:layout_constraintBottom_toBottomOf="parent"
            app:layout_constraintEnd_toEndOf="parent"
            app:layout_constraintStart_toStartOf="parent"
            app:layout_constraintTop_toTopOf="parent"
            app:layout_constraintVertical_bias="0.498" />
    
        <Button
            android:id="@+id/button3"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            app:layout_constraintBottom_toTopOf="@+id/place_holder"
            app:layout_constraintEnd_toStartOf="@+id/place_holder" />
    
        <Button
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            app:layout_constraintBottom_toBottomOf="@id/place_holder"
            app:layout_constraintLeft_toLeftOf="@id/place_holder"
            app:layout_constraintRight_toRightOf="@id/place_holder"
            app:layout_constraintTop_toTopOf="@id/place_holder" />
    </android.support.constraint.ConstraintLayout>
   
