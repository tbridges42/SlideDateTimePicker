SlideDateTimePicker
===================

SlideDateTimePicker is an Android library that displays a single 
DialogFragment in which the user can select a date and a time. 
The user can swipe between the DatePicker and TimePicker, and the tab 
underline will gradually animate as the user swipes. The colors of the 
tab indicator and divider lines are customizable to fit your project's 
theme.
This version of SlideDateTimePicker also includes a None button to allow 
your user to decline selecting a time and date. For the original 
version without a None button check out 
[jjobes' SlideDateTimePicker.](https://github.com/jjobes/SlideDateTimePicker) Tested on Android 4.0+.

<!--<img src="https://raw.github.com/jjobes/SlideDateTimePicker/master/screenshots/1.png" width="270" style="margin-right:10px;">
<img src="https://raw.github.com/jjobes/SlideDateTimePicker/master/screenshots/2.png" width="270">-->

Setup
=====

To add this library to your project, add the following to your `build.gradle`:

```groovy
dependencies {
    compile 'us.bridgeses:slideDateTimePicker:2.2.0'
}
```

How to Use
==========
(See [SampleActivity](https://github.com/jjobes/SlideDateTimePicker/blob/master/slideDateTimePickerSample/src/main/java/com/github/jjobes/slidedatetimepicker/sample/SampleActivity.java) for a more complete example)

First create a listener object:

```java
private SlideDateTimeListener listener = new SlideDateTimeListener() {

    @Override
    public void onDateTimeSet(Date date)
    {
        // Do something with the date. This Date object contains
        // the date and time that the user has selected.
    }
    
    @Override
    public void onDateTimeNone()
    {
        // The user has declined to select a date. Handle this as
        // appropriate.
    }

    @Override
    public void onDateTimeCancel()
    {
        // Overriding onDateTimeCancel() is optional.
    }
};
```

Then pass the listener into the builder and show the dialog:

```java
new SlideDateTimePicker.Builder(getSupportFragmentManager())
    .setListener(listener)
    .setInitialDate(new Date())
    .build()
    .show();
```

Note that the `Date` object that you pass in to `.setInitialDate()` should contain both the date and time that you wish to initially display.

**To set the minimum date to display:**

```java
.setMinDate(date)
```

**To set the maximum date to display:**
```java
.setMaxDate(date)
```

The default time format is the current device's default, but you can force a 24-hour or 12-hour time format:

**To force 24-hour time:**

```java
.setIs24HourTime(true)
```

**To force 12-hour time:**
```java
.setIs24HourTime(false)
```

**The default theme is Holo Light, but you can specify either Holo Light or Dark explicitly:**
```java
.setTheme(SlideDateTimePicker.HOLO_LIGHT)
```
or
```java
.setTheme(SlideDateTimePicker.HOLO_DARK)
```

**To specify the color for the sliding tab underline (indicator):**
```java
.setIndicatorColor(Color.parseColor("#FF0000"))
```

**To specify the color of the horizontal divider lines in the DatePicker and TimePicker:**
You can also set a custom color for the horizontal divider lines in the DatePicker and TimePicker, but for this you have to paste your own version of selection_divider.9.png into the the library's drawable-xxxx folders that has your desired color. To do this, open selection_divider.9.png in a graphics editor, change the color, then paste your new files into the drawable-xxxx folders.

Note on Reflection
==================
To allow for the modification of the horizontal dividers in the DatePicker and TimePicker, this library uses reflection in the CustomDatePicker and CustomTimePicker classes.

Contributing
============
Contributions are welcome. Please open up an issue in GitHub or submit a PR.

Changelog
=========

### v2.2.0

* Make width responsive to better support wider layouts

### v2.1.0

* More tests
* Adopt Continuous Integration

### v2.0.1

* Fix broken None button
* Add regression tests

### v2.0.0

* Switched away from support fragments
* Now requires API >= 17

### v1.1.0

* Made None button optional
* Made accent color change all line colors

### v1.0.0

* Forked from [jjobes' SlideDateTimePicker.](https://github.com/jjobes/SlideDateTimePicker)
* Added None button

License
=======
Licensed under the [Apache License, Version 2.0](http://www.apache.org/licenses/LICENSE-2.0.html)

The following files:

* SlidingTabLayout.java
* SlidingTabStrip.java 

are Copyright (C) 2013 The Android Open Source Project and are licensed under the Apache License, Version 2.0

Acknowledgements
================
Thanks to Jason Jobes for creating the original SlideDateTimePicker.

Thanks to Arman Pagilagan's [blog post](http://armanpagilagan.blogspot.com/2014/05/creating-custom-date-and-time-picker-in.html) for the initial idea.
