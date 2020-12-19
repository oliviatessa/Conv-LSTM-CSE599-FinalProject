# Next-Frame Prediction using Convolutional LSTM
CSE 599 Final Project - Olivia Thomas and Daniela Koch

## Protein Localization Dynamics in E.coli

It has been observed that the proteins within E.coli exhibit time dependent structure. This can be seen clearly in Figure 1 below, which shows the average position of a protein


<img src="cited_images/time_dependence_ex.jpg" height="200">  <img src="cited_images/time_dependence_ex copy.jpg" height="200">     

**Figure 1:** Demonstation of structured protein localization dynamics[[1]](#1)


Some of these proteins have been studied in detail, and it has been found that the observed structure is directly related to their function within the cell.  For example, the protein ftsZ can be found in highest concentrations at the middle of the cell, where it is responsible for the mechanics of cell division [[2]](#2).  We can gain intuition about proteins with unknown function by comparing their dynamical structure throughout the cell to those of proteins with known functions.


**Figure 1:** Demonstation of structured protein localization dynamics[[1]](#1)




- show example of consensus time dependence, now interested in single cell stuff, which is why we are interested in doing this with neual networks
- can we predict cell death? 
- can we predict mutations? 
- which protein dynamics are most indicative of cell health? 

## what is next frame prediction, how does it work?

### Background on ConvLSTM

The convolutional LSTM, first proposed in [1], uses convolutional operations instead of normal matrix operations in a LSTM recurrent network to capture both temporal and spatial dependencies in data. This algorithm has been used in video analysis, as well as in rainfall forecasting [1] and biological age prediction [Nature]. 

In this application, we adapt the pytorch convolutional LSTM implementation developed by https://raw.githubusercontent.com/ndrplz/ConvLSTM_pytorch/master/convlstm.py (ndrplz) to analyze time-dependent cell lifecycles. 

<img src="cited_images/lstm.jpeg" height="200">  <img src="cited_images/lstm_eqs.jpeg" height="150">     

**Figure :** Visual Representation of LSTM and associated equaions

<img src="cited_images/conv.jpeg" height="400">

**Figure :** Visualization of Convolutional Neural Network


<img src="cited_images/convlstm.jpeg" height="400">  

**Figure :** Visual Representation of Convolution LSTM 


<img src="cited_images/convlstm_eqs.jpeg" height="120">

**Figure :** 


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

https://papers.nips.cc/paper/2015/file/07563a3fe3bbe7e3ba84431ad9d055af-Paper.pdf

https://medium.com/neuronio/an-introduction-to-convlstm-55c9025563a7

https://www.nature.com/articles/s41598-019-46850-0

https://raw.githubusercontent.com/ndrplz/ConvLSTM_pytorch/master/convlstm.py
