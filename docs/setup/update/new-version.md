# Loop v1.5 Features

This is a new page in the docs.  Many people updating are not reading through the docs when they update their Loops, and therefore missing many of the new features (and requirements)...so we are adding a page to try to encourage docs use when updating.

As always though, the [GitHub page](https://github.com/LoopKit/Loop/releases/tag/v1.5.0) still has great release notes about the features and changes since the previous Loop v1.4

## OS updates

* **macOS Sierra**: macOS 10.12.6 Sierra at a minimum, but High Sierra will work, too.</br>
* **Xcode**: Xcode 9.2, older versions will not work </br>
* **iPhone**: iOS 10.3.3 at a minimum, but iOS 11.2.5 is the most current and works well.</br></br>


## Loop Settings

There are name changes to a couple old settings, and a new setting has been added.

<p align="center">
<img src="../img/new_settings.jpg" width="250">
</p>
</br></br>

****************************
###<p align="center">**Correction Range**</p>
</br>

Correction Range is the new name for what used to be called BG target range.  Reason being...correction range is a little more correct as the phrase represents the targets Loop is trying to correct you too...not necessarily what your ideal BG target range may be.  For example, you may keep a correction target of 100-100 for Loop to aim to, but use a desired BG target range of 90-150 when discussing things with your endo about "time in range".  Correction range is just a little more accurate about how the values are used.

****************************
###<p align="center">**Suspend Threshold**</p>
</br>

Suspend Threshold is the new term for the old Minimum BG Guard.  The name was changed to help people realize that this value is also used in determining when Loop will set zero temp basals (aka suspend basals) as well as its function in bolusing recommendations.  The description below the setting has been updated to help with that understanding.

****************************
###<p align="center">**Insulin Model**</p>
</br>

This section is brand new to Loop v1.5.  Loop still has the option for the old model (Walsh curve), as well as three new models.

You can read up on the new curves [here](https://loopkit.github.io/loopdocs/setup/loop-settings/settings/#insulin-model).  There is also a new customization section for the curves [here](/setup/build/code_customization.md#exponential-insulin-curve).

These new models are quite a bit different than the Walsh model.  I recommend watching the bolusing recommendations and how meals are behaving with your curve selection.  Because the timing of the peak activity has changed, this will impact how the Loop recommends boluses in some instances.  Overall, most users are finding that the changes have resulted in a bit more conservative bolusing recommendations (less insulin), especially for long slow carb meals.  Developers are looking at options to assess and address that.

If you fail to select an insulin model you will see this error "Missing data: Glucose effects"</br></br>

<p align="center">
<img src="../img/loop_select_model.jpg" width="250">
</p>
</br></br>

*************************

###<p align="center">**Pre-Meal Override Target**</p>
</br>

<p align="center">
<img src="../img/HUD.png" width="450">
</p>
</br></br>
You will notice a new logo of a plate with utensils next to the carb entry tool, at the bottom of the Loop main screen.  This icon will remain grey until you go into the Correction Targets area and set the "pre-meal" target range.  The pre-meal target is designed to be used to as an easy way to get a small amount of insulin delivered before a meal (similar to the "eating-soon" mode discussed in OpenAPS) in order to help control post-meal BG spikes.

<p align="center">
<img src="../img/premeal_entry.jpg" width="250">
</p>
</br></br>

If your normal target is 100-100 and pre-meal target is 80-80 mg/dl, for example, Loop will give you an extra push to get you to the lower target number before the meal.  The pre-meal target, when activated by pressing on the icon, will stay active for one hour, until carbs are entered, or until it is manually cancelled...whichever comes first.

Loop will adjust any insulin bolus as needed based on the insulin provided during this pre-meal time.

*************************

## Loop Use

###<p align="center">**Large Font**</p>
</br>

Users that had noticed increased font size setting in their iPhones were not rendering properly (as shown below)...this has been fixed in Loop v1.5

<p align="center">
<img src="../img/font_size_HUD.png" width="250">
</p>
</br></br>

*************************
###<p align="center">**Starting Bolus Indicator**</p>
</br>

A new status line will appear when Loop is sending a bolus command to the pump.  Just above the Glucose Chart, you will see a "stating bolus" indicator.

<p align="center">
<img src="../img/starting_bolus.png" width="250">
</p>
</br></br>

*************************
###<p align="center">**Automatic Dexcom Cloud Fetch**</p>
</br>

When local BG readings aren't being pulled by Loop, but are still fine on the Dexcom app, Loop will automatically switch to fetching from the Dexcom Servers to get BG data.  You will notice a small cloud above the BG reading when this occurs.

Deleting your transmitter ID for G5 users is no longer a useful troubleshooting step, since this change makes that switch happen automatically now.

<p align="center">
<img src="../img/server_pull.png" width="250">
</p>
</br></br>

*************************
###<p align="center">**Insulin Delivery in Health App**</p>
</br>

New to iOS 11 users, the Apple Health app will now track insulin delivery data.  Loop integrates with that feature.  A new docs page for Health app has been added too.  You can find more about that [here](/operation/features/healthapp.md)

<p align="center">
<img src="../img/todayhealth.jpg" width="250">
</p>
</br></br>

*************************

