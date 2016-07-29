# StylishWidget

**StylishWidget** is a library for an **Android Application project** to make the **UI more beautiful** and use **third party font**.
This library I use in my previous and current android project and may got an issue and error. 
I will keep improve this library until it stable and useful.

## Features
 * set custom font for almost all view.
 * Message Box
 * Progress Bar

Android 7.0+ support

## Download
 * **JAR** : (https://github.com/shiburagi/Stylish-Widget-for-Android/tree/master/stylishwidget/jar)
 * **APK** : (https://drive.google.com/file/d/0Bw_drx3o3plaZVptWWNxWUdfSmM/view?usp=sharing) 

## Including In Your Project
This library is presented as a `.jar` file which you can include in the `libs/`
folder of your application. You can download the latest version from the
[github repo](https://github.com/shiburagi/Stylish-Widget-for-Android/tree/master/stylishwidget/jar).

**or**,
you can include it by **download this project** and **import /stylishwidget** as **module**.

## Usage

**NOTE:** If you want to use **third-party font**, must **initialize** this line of code at the **top of onCreate() in main activity**, or at the **onCreate() of Custom** Application.

``` java
// parameter : Normal Font, Bold Font and Italic Font
Stylish.getInstance().set(
                fontFolder.concat("Rajdhani-Regular.ttf"),
                fontFolder.concat("Rajdhani-Bold.ttf"),
                fontFolder.concat("Rajdhani-Light.ttf"));
```
**or**
``` java
// parameter : Normal Font
Stylish.getInstance().setFontRegular(
                fontFolder.concat("Rajdhani-Regular.ttf")
);
// parameter : Bold Font
Stylish.getInstance().setFontBold(
                fontFolder.concat("Rajdhani-Bold.ttf")
);
// parameter : Italic Font
Stylish.getInstance().setFontItalic(
                fontFolder.concat("Rajdhani-Light.ttf"))
);
```



## Widget

![Screenshot](https://raw.githubusercontent.com/shiburagi/Stylish-Widget-for-Android/master/device-2016-07-19-211518.png)

to **use the widget**, is **same** like using **android widget**

**EditText**
``` xml
<com.app.infideap.stylishwidget.view.AEditText
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:hint="@string/editextexample" />
```

**TextView**
``` xml
<com.app.infideap.stylishwidget.view.ATextView
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:paddingLeft="5dp"
android:paddingRight="5dp"
android:text="@string/textviewexamplebold"
android:textAppearance="@style/TextAppearance.AppCompat.Medium"
android:textStyle="bold" />
```

**CheckBox**
``` xml
<com.app.infideap.stylishwidget.view.ACheckBox
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="@string/checkboxexample"/>
```

**RadioButton**
``` xml
<com.app.infideap.stylishwidget.view.ARadioButton
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:text="@string/radiobuttonexample"/>
```



## Button

![Screenshot](https://raw.githubusercontent.com/shiburagi/Stylish-Widget-for-Android/master/device-2016-07-19-211544.png)

``` xml
<com.app.infideap.stylishwidget.view.AButton
style="@style/Button.Default"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:text="Default" />
```



## Message Box

![Screenshot](https://raw.githubusercontent.com/shiburagi/Stylish-Widget-for-Android/master/device-2016-07-19-211608.png)

``` xml
<com.app.infideap.stylishwidget.view.MessageBox
android:id="@+id/message_info"
android:layout_width="match_parent"
android:layout_height="wrap_content"
app:boxBackground="@color/colorSuccess"
app:message="@string/helloworld" />
```

for the **MessageBox**, there are several **new declare-styleable** need to **highlight**,
* app:boxBackground - to set background color, only color allow.
* app:message - to set display text.
* app:textStyle - to set textView style, (normal, bold, italic).
* app:innerPadding - to set inner padding of message box.
* app:innerLeftPadding - to set inner left padding of message box.
* app:innerTopPadding - to set inner top padding of message box.
* app:innerRightPadding - to set inner right padding of message box.
* app:innerBottomPadding - to set inner bottom padding of message box.
* app:drawable - to set textView drawable.
* app:drawablePadding - to set padding of textView drawable.

and for **MessageBox** there are **two kind** of **listener or action mode**,

1) CloseButton, display as close icon
``` java
infoMessageBox.setCloseButton(new View.OnClickListener() {
  @Override
  public void onClick(View v) {
      AlertDialog dialog = new AlertDialog.Builder(MainActivity.this)
              .setMessage("Close Button Click!").create();
      dialog.show();

      infoMessageBox.setVisibility(View.GONE);
  }
});
```

2) ActionButton, display as outline button with a text
``` java
warningMessageBox.setActionButton(R.string.learnmore, new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        AlertDialog dialog = new AlertDialog.Builder(MainActivity.this)
                .setMessage("Warning Action Click!").create();
        dialog.show();
    }
});
```

however, only **one action** can be use for **a MessageBox**


## Progress Bar

![Screenshot](https://raw.githubusercontent.com/shiburagi/Stylish-Widget-for-Android/master/device-2016-07-19-211638.png)

**Sample code (XML):**
``` xml
 <com.app.infideap.stylishwidget.view.AProgressBar
            android:layout_width="match_parent"
            android:layout_height="30dp"
            app:maxValue="100"
            app:progressBackground="#ccc"
            app:progressColor="@color/colorAccent"
            app:progressText="30%"
            app:progressTextStyle="bold"
            app:progressValue="30"
            app:radius="7dp"
            app:withAnimation="true" />
```
Here the **list** of available attributes for progress bar,
``` xml
<attr name="maxValue" format="float" />
<attr name="progressValue" format="float" />
<attr name="radius" format="dimension" />
<attr name="progressColor" format="color" />
<attr name="progressText" format="string" />
<attr name="progressTextSize" format="dimension" />
<attr name="progressTextStyle" format="enum">
<enum name="normal" value="0" />
<enum name="bold" value="1" />
<enum name="italic" value="2" />
</attr>
<attr name="progressPadding" format="dimension" />
<attr name="progressIconPadding" format="dimension" />
<attr name="withAnimation" format="boolean" />
<attr name="duration" format="integer"/>
<attr name="progressTextAppearance" format="reference"/>
<attr name="progressBackground" format="color"/>
<attr name="progressIcon" format="reference"/>
```
and, here the list of all declare function in AProgressBar class,
``` java
setProgressBackground(int color) 
getProgressValue()
getProgressValue(int index)
setPadding(int padding)
setMaxValue(float value)
setProgressValue(float value)
setProgressValue(int index, float value)
setProgressValues(float ...values)
addProgressValue(float value)
addProgressValue(float value, int color)
removeProgressValue(int index)
setProgressColor(int color)
setProgressColor(int index, int color)
setProgressColors(int ...colors)
setProgressValueWithColor(int index, float value, int color)
setProgressText(int resId)
setProgressText(String text)
setProgressText(int index, int resId)
setProgressText(int index, String text)
setProgressTexts(int ...resId)
setProgressTexts(String ...texts)
setProgressValueAndText(int index, float value, int resId)
setProgressValueAndText(int index, float value, String text)
setProgressIcon(int resId)
setProgressIcon(Drawable icon)
setProgressIcon(int index, int resId)
setProgressIcon(int index, Drawable icon)
setProgressIcons(int ...resId)
setProgressIcons(Drawable ...icons)
setGravity(int gravity)
withAnimation(long duration)
setProgressTextStyle(int textStyle)
setProgressTextAppearance(int resId)
setProgressIconPadding(int padding)
```

### Example for multiple progress bar,
``` java
AProgressBar iconMultiProgressBar =
        (AProgressBar) view.findViewById(R.id.progressBar_multi_icon);
iconMultiProgressBar.setProgressValues(
        30,
        150,
        90,
        70);

iconMultiProgressBar.setProgressColors(
        Color.parseColor("#039BE5"),
        Color.parseColor("#8BC34A"),
        Color.parseColor("#FBC02D"),
        Color.parseColor("#f44336"));

iconMultiProgressBar.setProgressTexts(
        "30%",
        "150%",
        "90%",
        "70%"
);
iconMultiProgressBar.setProgressIcons(
    R.drawable.ic_directions_run_white_24dp,
    R.drawable.ic_directions_bike_white_24dp,
    R.drawable.ic_directions_boat_white_24dp,
    R.drawable.ic_directions_subway_white_24dp
);

iconMultiProgressBar.setMaxValue(100);
iconMultiProgressBar.withAnimation(1000);
```
For more **progress bar example**, please refer on the link below :

https://github.com/shiburagi/Stylish-Widget-for-Android/blob/master/app/src/main/java/com/app/infideap/mystylishexample/ProgressBarFragment.java

## Contact
For any enquiries, please send an email to tr32010@gmail.com. 

## License

    Copyright 2016-2017 Shiburagi

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
