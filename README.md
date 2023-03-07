# A DATASET for GPS Spoofing Detection on Autonomous Vehicles
#### Authors
Ghilas Aissou, Selma Benouadah, Hassan El Alami, and Naima Kaabouch
#### Affiliations
School ofElectrical Engineering andComputer Science, University of North Dakota Grand Forks, ND 58202
USA
#### Corresponding author’s email address
ghilas.aissou@und.edu
### Abstract
A dataset of Global Positioning System (GPS) spoofing attacks is presented in this article. This dataset includes data extracted 
from authentic GPS signals collected from different locationsto emulate a moving and a static autonomous vehicle using a universal
software radio peripheral unit configured as a GPS receiver. During the data collection, 13 features are extracted from eight-parallel 
channels at different receiver stages (i.e., acquisition, tracking, and navigation decoding). In addition to the collected authentic GPS 
signals, three GPS spoofing attack types were simulated, simplistic, intermediate, and sophisticated attacks. The resultant dataset 
contains a total of 158,170 samples, including 55% of legitimate instances and 45% of samples corresponding to three types of 
simulated GPS spoofing attacks, all in a balanced distribution. The data described and attached to this article can be used to 
investigate the effect of the GPS spoofing attack on the extracted features and contribute to the development of GPS spoofing attack 
detection techniques based on supervised and unsupervised machine learning.

### Value of the Data
- The raw dataset is collected using real-time feature extraction from authentic GPS signals using a USRP unit configured as 
an eight-channel GPS receiver emulating a real GPS receiver in an autonomous vehicle. The dataset includes the correlator's 
amplitude at the time the Doppler shift is updated.
- Using the collected GPS signals, three spoofing attack types were simulated: simplistic, intermediate, and sophisticated 
attacks. A simulation was chosen over real live GPS spoofing attacks since they are illegal and risky, and setting up an indoor 
test bench was dismissed as its results are often biased and incorrect.
- The dataset is made easy for robust training of supervised/unsupervised machine learning algorithms to detect GPS spoofing 
attacks by converting the 3D cubic data from the eight parallel channels into a 2D feature map.
- The three different attacks and legitimate signals can easily be separated from each other using the label field. In this way, 
the dataset can be rearranged for binary classification with one attack at a time.
- The dataset is available in Excel format and can be converted to a comma-separated file format to help researchers easily 
import the dataset into different research software platforms and programs.
- A separate Excel file containing the raw (original) GPS data is included for researchers to use to simulate customized GPS-related attacks or for other uses.
- As civilian GPS transmissions are open and unencrypted, GPS spoofing attacks against GPS receivers are frequent and 
dangerous. Researchers can utilize this dataset to study how different extracted features impact Artificial Intelligence (AI) 
based models' ability to identify and categorize spoofed and real instances. The research based on this dataset will then help 
the community develop robust countermeasures for GPS spoofing attacks.

### Data Description 
 
#### 1.1. Data Collection
The data was collected using a GPS receiver in two different scenarios. The first is a driving test at speeds ranging from 0 to 60 mph 
with an average speed of 45 mph. The second scenario consists of three stationary positions at different altitudes. It is worth 
mentioning that the vertical GPS position error is larger than the horizontal plane since a sufficient satellite spread is only possible 
for a horizontal plane [1].
<figure>
<p align="center">
  <img src="https://github.com/ghilasaissou/A-DATASET-FOR-GPS-SPOOFING-DETECTION-ON-AUTONOMOUS-VEHICLES/blob/main/Screenshot%202022-11-21%20192901.png">
 <figcaption align = "center"><b> Fig.1 - Two scenarios of GPS signal collection, a static GPS receiver in three different locations 
                                    (on the right), and a driving scenario (on the left) </b></figcaption>
</p>
</figure>
The collected data is offered in two different formats, an 8-channel format and a readable (simple/ efficient)
format rendered in excel files. The 8-channel format consists of 158,170 data samples with 13 features from
eight channels represented as a 3-dimensional expansion of the channels, as illustrated in Fig. 2. The extracted
2
features and their corresponding stage of extraction are described in Table 2. The extraction process is done in
parallel in each of the eight channels.

<figure>
<p align="center">
  <img src="https://github.com/ghilasaissou/A-DATASET-FOR-GPS-SPOOFING-DETECTION-ON-AUTONOMOUS-VEHICLES/blob/main/Screenshot 2023-03-07 134737.png">
 <figcaption align = "center"><b> Fig.2 - Parallel feature extraction from 8 channels GPS receiver </b></figcaption>
</p>
</figure>

The readable excel format is a conversion of the time series output data of the eight channels receiver into
a non-time series distribution. The zero values in the 8-channel dataset represent the time interval where the
channels are unlocked with the GPS signals, thus all those values are removed in the simplified format.

| Feature name  | Second Header |
| ------------- | ------------- |
|The satellite vehicle number (PRN) |Post-correlation|
|The Carrier Doppler in HZ (DO) |Post-correlation|
|Pseudo-range in meter (PD) |Post-correlation|
|Receiver Time (RX) |Post-correlation|
|Time of the week in second (TOW)| Post-correlation|
|Carrier Phase Cycles (CP) | Post-correlation|
|The magnitude of the Early Correlator (EC)| During correlation|
|The magnitude of the Late Correlator (LC) |During correlation|
|The magnitude of the Prompt Correlator (PC)| During correlation| 
|Prompt in phase correlator (PIP) |During correlation|
|Prompt Quadrature component (PQP)| During correlation|
|Carrier Doppler in Tracking loop (TCD)| During correlation|
|Carrier to noise Ratio in dB (C/N◦)| Pre-correlation|
 
 #### 1.2 Features description
**PRN:** The GPS constellation contains 27 operational satellites, each satellite is identified with a unique identification number.  <br>     
**DO:**The Doppler shift isthe result of the satellite and receiver motion. The DO is expressed asthe frequency drift between the sent
frequency and received frequency of the GPS signal, as described in (1). <br> 
$f = (\frac{c+v_r}{c+v_s}) \times f_i $    (1)   <br> 
Where, vr is the receiver speed, and vs is the satellite speed [2]. The Doppler offset is ±5kHz with rate of
change of ±20Hz related to the receiver configuration. <br> 
**PD:** The pseudo-range is the time difference between the transmission and reception time. It can be expressed
in meter which refer to the distance between the receiver and the satellites. PD is given by (2)
\begin{equation}
P_s = c(t_r - t_s)
	\label{pdEquation}
\end{equation}

