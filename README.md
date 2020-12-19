# Next-Frame Prediction using ConvolutionalLSTM
CSE 599 Final Project - Olivia Thomas and Daniela Koch

## background on cell stuff

- Proteins in cells exhibit structure
- Proteins are responsible for pretty much all cell processes, so knowing about their function

## what is next frame prediction, how does it work?

### Background on ConvLSTM


## More detailed problem overview 

### Data 


The data used in this project is part of a publicly available set of 

The images in were segmented using the SuperSegger[[1]](#1) software created by the Wiggins lab. The software and full documentation for the image segmentation can is publicly available and can be found here: https://github.com/wiggins-lab/SuperSegger/wiki. 


![Celltower1](example1.png)


### Data Preprocessing
After segmentation (make all lifecycles same length, cells same size, etc)
Do this to make it easier for network to learn the thing we actually care about, which is the internal dynamics 




## References
<a id="1">[1]</a> 
Stylianidou, S., Brennan, C., Nissen, S.B., Kuwada, N.J. and Wiggins, P.A. (2016), SuperSegger: robust image segmentation, analysis and lineage tracking of bacterial cells. Molecular Microbiology, 102: 690-700. https://doi.org/10.1111/mmi.13486

