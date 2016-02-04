## daynoleap2datenum.m

Many of the climate and earth system models used in my field of research use a 365-day calendar for their simulations.  When working with the output in Matlab, and trying to compare simulations to real-world data, the mismatch between the real-world calendar and the model calendar can cause frustration. 

This function makes it easier to compare such datasets, and allows you to use Matlab's date-related functions, which expect time variables to be presented as either serial date numbers or datetime objects.  Note that this is simply intended for cosmetic purposes; in the final output, all Feb. 29ths are skipped, so be careful when doing things like calculating durations in the resulting timeseries vs. the original model timeseries.

In this example, note the difference between day 0 and day 364, as well as the dates around Feb 29, 2000 (a leap year), when using this function vs simple addition to the t = 0 of Jan 1, 2000:

```matlab
t = [0 58:60 364]';
t1 = datetime(2000,1,1) + t
t2 = daynoleap2datenum(t, 2000, 'dt')
```

```
t1 = 

   01-Jan-2000 00:00:00
   28-Feb-2000 00:00:00
   29-Feb-2000 00:00:00
   01-Mar-2000 00:00:00
   30-Dec-2000 00:00:00


t2 = 

   01-Jan-2000 00:00:00
   28-Feb-2000 00:00:00
   01-Mar-2000 00:00:00
   02-Mar-2000 00:00:00
   31-Dec-2000 00:00:00
```

