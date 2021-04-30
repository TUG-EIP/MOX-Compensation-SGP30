# MOX-Compensation-SGP30

In this repository, we provide the data we have used to compensate sensitivity changes of duty-cycled MOX gas sensors with machine learning. Details about our work can be found in [our paper](https://linktopaper).

## Datasets

In the folder `data`, we provide 5 different datasets. Each dataset contains data from 3 SGP30 sensors running simultaneously. Device1 was operated continuously, device2 was operated on-demand with an on-time of 5 seconds and random off-times and device3 was duty-cycled with an on-time of 5 secons and a period of 5 minutes.

Name | Duration [h] | #samples [device1] | #samples [device3] | #samples [device2] 
-|-|-|-|-
`dataset_train_test` | 144 | 51485 | 1728 | 1700
`dataset_test_04d` | 96 | 34325 | 1152 | 1099
`dataset_test_18d` | 63 | 22768 | 764 | 780
`dataset_test_22d` | 72 | 27133 | 911 | 949
`dataset_test_53d` | 96 | 326164 | 1152 | 1944

Additionally, we have included plots visualizing each dataset, where we plot each sample from the continuous datasets and the last value of each sample from the duty-cycle and on-demand datasets.

## Dataset Structure

The dataset `csv` files have the following header:

`time,rel. Time,tVOC,CO2eq,Ethanol,H2,Temperature,Rel. Humidity`

- `time` describes the absolute time-stamp
- `rel. Time` was used internally as a relative time-stamp
- `tVOC` describes the tVOC measurement
- `CO2eq` describes the CO2eq measurement
- `Ethanol` describes the Ethanol measurement
- `H2` describes the H2 measurement
- `Temperature` describes the temperature measurement
- `Rel. Humidity` describes the relative humidity measurement

The samples from the datasets can be read as followed:

### Continuous (device1) datasets:

Each sample is terminated with a row starting with an `end` identifier. The row before describes the measurement values. The measurement values are duplicated in the `end` row for convenience.

### Duty-cycle (device3) and on-demand (device2) datasets:

Each sample is terminated with a row starting with an `end` identifier. The rows before describe the measurements taken during the on-time of the device with `36Hz`. In these modes, there are no `tVOC` and no `CO2eq` measurements available. Temperature and relative humidity can be extracted from the `end` row.

## Contact

Feel free to contact us for any questions on the data or to present your findings on this topic to us. We are curious to hear about your work!
