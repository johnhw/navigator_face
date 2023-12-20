# navigator_face
A celestial navigation face for Sensorwatch. This and a sextant is sufficient to navigate fairly accurately. It's recommended to use the [nanosec watch face]() to get an accurate chronometer time with this face.

# Features
* Sights from sun, moon, the visible planets and the 57 navigational stars
* Can automatically update position, or give details for drawing LOPs on a traditional chart
* Dead-reckoning based updates
* Alamanac *and* a sight reduction table in one.
* A history of fixes is kept (including DR and known locations)
* (optional) auto-selection of visible/good celestial bodies
* Kalman filter based estimation of location with uncertainty
* "Show your working" mode to show full steps in fixing.

# How to use the face
The watch face uses the watch's lat/long location registers -- it reads and writes them as positions are updated. This means that other faces that use positions will track the fixed position.

## Modes
The navigation face has three modes:
* `POS` mode, that shows where you are (i.e. lat/lon), and can also show the certainty of that estimate (radius of uncertainty).
* `FIX` mode, that can add a new fix to the history.
* `HISTORY` mode, that allows you to view (and edit) the history of fixes.

## History mode
The history is the most complex mode. It allows a history of sights and fixes to be kept.

* The last 100 fixes are kept in a history.
* Each fix has a type (e.g. celestial, PP, DR) and the relevant information about that sight.
* Fixes can be viewed in detail, including seeing the sight values and stepping through all of the standard calculations.
* If you realise a past entry was bad, you can delete or edit it; the subsequent position fixes will be recomputed.

A history entry has:
* an **index** 00-99
* a **timestamp** inc. time and date
* a **type** (DR, PP, Su, Mo, 23, etc.)
* sight data

## Taking a fix
* Enter FIX mode
* Select the celestial body. Press ALARM.
* Watch will flash `SI tE`.
* Take the sight. Immediately press ALARM. The watch will long beep.
* (If you messed up the sight, long press ALARM until CNCL appears, then long press ALARM again. This will discard the sight. Short pressing ALARM will cancel the discard.)
* Press LIGHT to toggle upper/lower limb (will be lower limb by default).
* Press ALARM to confirm the limb.
* Set the sextant reading in `DD Dm md` format. Long press ALARM to confirm.
* That's it! You'll be back in POS mode, and can see your estimated lat/lon

## Updating DR
* Enter FIX mode
* Select `DR`. Press ALARM.
* Enter your estimated course in (whole) degrees true. `3 21` is 321 degrees *true*. `CO` appears at the top.
* Enter your estimated speed in decimal knots (e.g. 5.2). Maximum speed is 69.9 knots. `04 2` is 4.2kts. `SP` appears at the top

## Updating PP
* Enter FIX mode
* Select `PP`. Press ALARM.
* Enter your latitude `LA`
* Enter your longitude `LO`
* Enter your precision `Pr`. Options are "0M" (exact=1/10th minute) "1M" (=1 minute), "5M" (=5 minutes), "15M"=(15 minutes), "30M" = (1/2 degree), "1D" = (1 degree), "5D" = (5 degree), "15D" = (15 degree), "90D" = 90 degree


## Types of fixes
* Celestial
  *  `Su` Sun
  *  `Mo` Moon
  *  `Ma` Mars
  *  `Ve` Venus
  *  `Sa` Saturn
  *  `Ju` Jupiter
  *  `Me` Mercury
  *  `01-57` the [Navigational stars](https://en.wikipedia.org/wiki/List_of_stars_for_navigation)
  *  `Po` Polaris
* Dead reckoning DR
  * `DR` fixes include a speed (kts) and heading (degrees).
* Known position PP
  * `PP` fixes include a position and an error estimate (e.g. is the fix good to a hundredth of a minute, or to five degrees?)

# User interface
