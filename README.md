# Smartphone Price Estimator

## Data Source - 
- Around 10k data points in total with 86 features <br>
Link - https://www.kaggle.com/msainani/gsmarena-mobile-devices

## Key Variables used - 
### Categorical Variables
1. oem (Brand)
2. network_technology
3. platform_os
4. main_camera_video

### Flag variables
1. network_gprs (yes vs no)
2. network_edge (yes vs no)
3. launch_status (discontinued vs avialable)
4. body_sim (dual vs single)
5. sound_loudspeaker (yes vs no)
6. comms_wlan (yes vs no)
7. comms_bluetooth (yes vs no)
8. comms_radio (yes vs no)
9. comms_gps (yes vs no)
10. network_2g_bands (value vs null)
11. network_3g_bands (value vs null)
12. network_4g_bands (value vs null)
13. network_5g_bands (value vs null)
14. main_camera_five/quad/triple (yes vs no)

### Numeric variables 
1. launch_announced (2020 - year of launch)
2. body_dimensions (dimension1 * dimension2 * dimension3)
3. body_weight (weight1 * weight2)
4. display_resolution (resolution1 * resolution2)

### Target var 
- misc_price (Price)


## Preprocessing
1. For flag variables - Fill missing values and 'No' with '0', rest all is treated as '1'
2. Categories used for OS - Android, iOS, Windows, Others
3. Categories used for main_camera - 8K, 4K, 2160p, 1080p, 720p, 480p, 320p, Others
4. Categories used for network - No cellular connectivity, GSM, 5G,	EVDO, LTE, UMTS, CDMA2000, HSPA, CDMA
5. For launch date, numeric value is calculated using (2020 - launch year). Lower the value, more latest the phone is.
6. Dimensions, weight, and resolution variables are treated as numeric values
7. Target value is calculated by taking only clean misc_price values available. EUR and INR value is converted to USD for equal comparison.

## Modeling
1. XGBoost Regressor is used to calculate the price with minimal hypertuning.
2. Train-test is split in 3:1 ratio.
3. Model is evaluated with mean squared error which comes approx 6500. A dummy model was created which only predicts $200 for all phones to compare the accuracy of our current model. The dummy model gave a mean squared error of 21000.
