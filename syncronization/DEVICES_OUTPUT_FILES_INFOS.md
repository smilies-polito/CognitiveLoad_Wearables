# DEVICES OUTPUT FILES INFOS

## Empatica Embrace Plus

Empatica Embrace Plus is worn on the wrist. Its native output avro files contain accelerometer, gyroscope, eda, temperature, bvp, systolicPeaks, steps, magnetometer, AmbientLight fields.

The avro files were converted into json files with all these fields (into {} rawData), but only bvp, eda and accelerometer data were considered and checked, no info will be provided on remaining fields. Each json raw data field has the keys "timestampStart" and "samplingFrequency" that allow for synchronization.

## Polar H10

Polar H10 is chest worn. The data were streamed live through an app. The files obtained are txt with these columns: Phone timestamp; sensor timestamp [ns]; timestamp [ms]; ecg [uV].

The phone timestamp is in fromat YYYY-MM-DDTHH:MM:SS.sss), Europe/Rome timezone and should be used for syncing. Sampling Frequency is 130 Hz but can be manually extracted from timestamp differences.

## Shimmer GSR+

Shimmer GSR+ is worn on the wrist with a strap. From the box on the wrist, sensors are placed on fingers for EDA recording and finger/earlob for BVP recording. This also means that motion data (accelerometer, gyroscope and magnetometer) are recorded from the wrist position (sensors in the box). Data were obtained from Consensys platform. The csv files contains these columns: Shimmer_4086_Timestamp_Unix_CAL, Shimmer_4086_Accel_LN_X_CAL, Shimmer_4086_Accel_LN_Y_CAL, Shimmer_4086_Accel_LN_Z_CAL, Shimmer_4086_GSR_Range_CAL, Shimmer_4086_GSR_Skin_Conductance_CAL, Shimmer_4086_GSR_Skin_Resistance_CAL, Shimmer_4086_Gyro_X_CAL, Shimmer_4086_Gyro_Y_CAL, Shimmer_4086_Gyro_Z_CAL, Shimmer_4086_Mag_X_CAL, Shimmer_4086_Mag_Y_CAL, Shimmer_4086_Mag_Z_CAL, Shimmer_4086_PPG_A13_CAL, Unnamed: 14.

We considered Shimmer_4086_GSR_Skin_Conductance_CAL (EDA), Shimmer_4086_PPG_A13_CAL (BVP), and Shimmer_4086_Timestamp_Unix_CAL for timestamp synchronization. The sampling frequency is 128Hz.

*Note on acronyms:* PPG = photoplethysmography, the optical sensing modality used to record the signal; BVP = blood volume pulse, the physiological signal derived from PPG and used as a synonym in this repository; EDA = electrodermal activity; ECG = electrocardiogram; PVSAT = Paced Visual Serial Addition Test; NASA-TLX = NASA Task Load Index.
