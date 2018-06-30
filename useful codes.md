All the referring are done from [this repository](https://github.com/hakansrc/mlv_inv) if the links are not working, You can visit the repository's previous version. (i.e. before 30.06.2018)
### For Spectrum Analysis

**Following code can be used to plot spectrum of a signal.**

`N = numel(threelevelspwm_p.get('DCLINK_voltage').signals.values); <br />
DCLINK_upperc_voltage_spectrum = fft(threelevelspwm_p.get('upperc_voltage').signals.values,N)/(0.5*N);<br />
DCLINK_upperc_voltage_spectrum_abs = abs(DCLINK_upperc_voltage_spectrum(1:(N/2+1)));<br />
DCLINK_upperc_voltage_spectrum_abs(1) = DCLINK_upperc_voltage_spectrum_abs(1)/2;<br />
freq = (0:(N/2))*Fs/N; % Fs: Sampling Frequency<br />
plot(freq,DCLINK_upperc_voltage_spectrum_abs)`

**[This code](https://github.com/hakansrc/mlv_inv/blob/master/topologies%20to%20be%20evaluated/capacitorselection.m) can be used for capacitor selection, for more information please contact [Mesut Uğur](https://github.com/mesutto)**<br />

