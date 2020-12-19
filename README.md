# Next-Frame Prediction using ConvolutionalLSTM
CSE 599 Final Project - Olivia Thomas and Daniela Koch

## background on cell stuff

It has been observed that the proteins within E.coli exhibit time dependent structure.  Some of these proteins have been studied in detail, and it has been found that the observed structure is directly related to their function within the cell.  For example, the protein ftsZ can be found in highest concentrations at the middle of the cell, where it is responsible for the mechanics of cell division [[2]](#2).  We can gain intuition about proteins with unknown function by comparing their dynamical structure throughout the cell to thoseof proteins with known functions.



![SeggerExample](cited_images/time_dependence_ex.jpg)  <br />
**Figure 1:** Demonstation of structured protein localization dynamics[[1]](#1)




- show example of consensus time dependence, now interested in single cell stuff, which is why we are interested in doing this with neual networks
- can we predict cell death? 
- can we predict mutations? 
- which protein dynamics are most indicative of cell health? 

## what is next frame prediction, how does it work?

### Background on ConvLSTM

## More detailed problem overview 

### Data 


The data used in this project is part of a publicly available set of 

The images in were segmented using the SuperSegger[[2]](#2) software created by the Wiggins lab. The software and full documentation for the image segmentation can is publicly available and can be found here: https://github.com/wiggins-lab/SuperSegger/wiki. This software allows us to not only automatically segment the i   


![SeggerCycle](cited_images/seggerLifetime.jpeg)
**Figure :** Example of automatic cell segmentation performed by SuperSegger [[2]](#2)*

![SeggerExample1](cited_images/superseggerexample.jpg)
**Figure :** Single-cell lifecycle tracking over time [[2]](#2)*

After all the segmentation, we get images like these.

![Celltower3](cited_images/ftszexample.png)  ![Celltower1](cited_images/example1.png)   ![Celltower2](cited_images/example2.png)

### Data Preprocessing
After segmentation (make all lifecycles same length, cells same size, etc)
Do this to make it easier for network to learn the thing we actually care about, which is the internal dynamics 

-normalizing the cell cycle (size of cell and number of stages in cycle)

![SeggerExampleNorm](cited_images/cyclenormalization.jpg)
**Figure :** Consensus tower normalizes cell shape, size, and lifecycle-length


### Final Data used in network
Our final pre-processed data is comprised of samples each containg the padded images for each stage of the cell-cycle. More specifically, the input to the network is a pytorch tensor containing (bath_size, seq, channels, height, width)


![finaldatafr1](aska1aN/xy01Cell0000416/Cell0000416_frame_1.png)
**Figure:** Final data



## Our Network

Hyperparameters
- Batch size: 128
- Number of Epochs: 

- Training Samples:
- Validation Samples:
- Test Samples: 
- Image augmentations: horizontal flip, vertical flip, both



## Results


## References
<a id="1">[1]</a> 
Kuwada, N.J., Traxler, B. and Wiggins, P.A. (2015), Protein localization dynamics in bacteria. Molecular Microbiology, 95: 64-79. https://doi.org/10.1111/mmi.12841

<a id="1">[2]</a> 
Stylianidou, S., Brennan, C., Nissen, S.B., Kuwada, N.J. and Wiggins, P.A. (2016), SuperSegger: robust image segmentation, analysis and lineage tracking of bacterial cells. Molecular Microbiology, 102: 690-700. https://doi.org/10.1111/mmi.13486

