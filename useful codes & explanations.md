All the referrings are done from [this repository](https://github.com/hakansrc/mlv_inv) if the links are not working, You can visit the repository's previous version. (i.e. before 30.06.2018)
### For Spectrum Analysis

**Following code can be used to plot spectrum of a signal.**

`N = numel(threelevelspwm_p.get('DCLINK_voltage').signals.values); <br />
DCLINK_upperc_voltage_spectrum = fft(threelevelspwm_p.get('upperc_voltage').signals.values,N)/(0.5*N);<br />
DCLINK_upperc_voltage_spectrum_abs = abs(DCLINK_upperc_voltage_spectrum(1:(N/2+1)));<br />
DCLINK_upperc_voltage_spectrum_abs(1) = DCLINK_upperc_voltage_spectrum_abs(1)/2;<br />
freq = (0:(N/2))*Fs/N; % Fs: Sampling Frequency<br />
plot(freq,DCLINK_upperc_voltage_spectrum_abs)`

**[This code](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/capacitorselection.m) can be used for capacitor selection, for more information please contact [Mesut Uğur](https://github.com/mesutto)**<br />


For gathering data we have used the Matlab and Simulink routines in [this file](https://github.com/hakansrc/mlv_inv/tree/master/topologies%20to%20be%20evaluated)
The functions are used for determination of output power, capacitor value, ma values etc. for each topology that are investigated in [this paper](https://github.com/mesutto/IMMD/blob/master/Paper/PEMC%202018/Final%20Paper/PEMC2018_FinalPaper.pdf). Note that in the codes topologies are tagged as A B C D E for convenience.

<br />[commenouter.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/commentouter.m) function is used for comment outing the unnecessary blocks. For example, when topology A is working in the simulation, everything that are related to the other topologies are commented out

[alltopologies.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/alltopologies.m) is the main code that calls all the functions and runs the simulink file [all_topologies.slx](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/all_topologies.slx) 

[dataselector.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/dataselector.m) function is used for the determination of the datas to be collected. When the values of the variables in [alltopologies.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/alltopologies.m) from row 25 to 35 are changed, the related datas are either collected and saved or not.

[datacollector.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/datacollector.m) function is not used.

[loadsourcesettings.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/loadsourcesettings.m) function is used for the setting the load and source values for diffent topologies at different loads.

[loopdecider.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/loopdecider.m) function is used for running the related simulink file which is [all_topologies.slx](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/all_topologies.slx)

[powervariation.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/powervariation.m) function is used for setting the load and sources for the power variation cases.

[topology_decider.m](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/topology_decider.m) function is used for commenting out or uncommenting main blocks that are in [all_topologies.slx](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/all_topologies.slx) 
