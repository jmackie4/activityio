# Version 0.0.3
+ `ActivityData` has some new methods:
    - The GoldenCheetah/Skiba 'xPower' metric (`xpwr()`)
    - `pwr_prof()` for power profiling. This uses the new `PowerProfile` type.
    - `recording_time()` for calculating actual time spent in an activity.
+ .fit file timestamps weren't being handled correctly; now they are. And you can now 'localise' them from UTC time (default) by passing in a timezone string. Closes #1.
+ .tcx files don't expect fractional seconds by default (closes #2).
+ The `tools` module now has an `ewa` (exponentially weighted average) function, which returns a callable intended for the `.rolling().apply()` interface of `pandas`.
+ The `PowerProfile` type (created via the `pwr_prof()` method on an `ActivityData` instance) makes performance profiling straightforward. Particularly across a number of files.
+ Restructured the code base as type definitions needed their own subpackage, rather than just a module.
+ Refactored some of the reading process for xml file types.
+ Corrected a syntax error in the command line interface.
+ More general exception catching in `ActivityData.__getitem__` so as not to interfere with the parent method.
+ Creating a `Gradient` column via the `ActivityData.gradient()` method was dropping the index. This is fixed.
+ `ActivityData.resample_1hz()` is gone as it was overkill. Call the `pandas` API instead.
+ Dependencies inherited from `pandas` are now included explicitly.
+ Various bug fixes.

# Version 0.0.2
+ Support added for *.gpx files.
+ Command line interface added (see `aio -h`).
+ `activityio._util.xml` was clobbering the standard library package in some cases, so was renamed to `activityio._util.xml_reading`
+ Non-code files removed from packages.

# Version 0.0.1
+ Alpha version released.

___
# TODO:
+ Make sure that `DataFrame` methods on `ActivityData` return an `ActivityData` instance.
+ Make tests executable via `pip`.