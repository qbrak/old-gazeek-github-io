# gazeek.github.io
Piotr Held's  website/blog

I don't know where to put this, so here is my list of useful links:

# PCA
* Tutorial https://arxiv.org/pdf/1404.1100.pdf

# Stats
* Great website with lots of stats stuff: https://www.statlect.com/
* Variance estimate of normal distribuition: https://www.statlect.com/fundamentals-of-statistics/variance-estimation#:~:text=Variance%20estimation%20is%20a%20statistical,estimator%20of%20the%20population%20variance.
* Stdev estimate of stdev: https://stats.stackexchange.com/a/28567

# DSP
Really cool book about DSP: https://www.dspguide.com/

Here is an article about random sampling: https://arxiv.org/pdf/1204.0839.pdf

Here is an article about time-interleaved sampling: https://www.analog.com/en/analog-dialogue/articles/interleaving-adcs.html#:~:text=Time%20interleaving%20is%20a%20technique,of%20each%20individual%20data%20converter

Correcting the distortion caused by window function: https://community.sw.siemens.com/s/article/window-correction-factors
(however, coherent gain (a.k.a. DC gain) assumes that sum(win)!=1, if sum(win)=1, then coherent gain=1).

## Wavelets
* A guide about wavelet tranform (has 4 parts): https://ccrma.stanford.edu/~unjung/mylec/WTpart1.html

## Random processes
* Deriving frequency response of a instantiation of a random process passed through a window: https://radarsp.weebly.com/uploads/2/1/4/7/21471216/dft_of_noise.pdf
* How to interpret power density spectra of random processes: https://www.sgu.ru/sites/default/files/textdocsfiles/2014/10/29/random_proc_slides_5_psd_2pages.pdf
* Lecture on different methods of estimating power density spectra of random process (periodogram, Bartlett and Welch's methods): http://www.laurent-duval.eu/Documents-Common/Schuster_G_2010_lect_spectrum_upbw.pdf
* Standford lectures on DSP, in particular section on pink noise: https://ccrma.stanford.edu/~jos/sasp/Example_Pink_Noise_Analysis.html

Some notes on estimating power spectrum density for random process:

We could potentially estimate the autocorrelation function (e.g. through averaging) and then FFT that and get the PSD for the random process, however, it seems that direct calculations of periodograms and averaging them is the preferred method from a calculation standpoint.

# Electronics

* This looks like a really cool electronics book: https://ultimateelectronicsbook.com/#introduction
* Impedances, Thevenin can be used not only to model electrical systems: http://web.mit.edu/2.151/www/Handouts/Impedances.pdf
