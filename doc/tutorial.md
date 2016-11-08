## Tutorial: Extract the time courses of respiration and heart contraction
(The MRI movie is courtesy of Jens Frahm and coworkers at Max-Planck-Institut f�r
Biophysikalische Chemie in G�ttingen and is available at:
[http://www.biomednmr.mpg.de/index.php?option=com_content&task=view&id=132&Itemid=38#Cardio](http://www.biomednmr.mpg.de/index.php?option=com_content&task=view&id=132&Itemid=38#Cardio)  
### 1. Do PCA on the movie  
Select the movie named as `cardiac-rtMRI.avi` in the unzippped 
`TRENDexample` folder. Run PCA using `trendmaingui` with row scaling method 
set as `noscaling`,  and `reconstruct` option turned on to save files for
reconstruction.  
![trendmain](https://bytebucket.org/chia_hsu/trend/raw/fb28422bb0533953c364427db8315a33e0cd415b/docs/png/png_tutorial/1_trendmain.png?token=953a23fe763e1ee6450967e21d016d8d9e54f92e)  
To do this at the command line, `cd` to the directory where the 
`cardiac-rtMRI.avi` is, and run:  
`trendmain.exe -f cardiac-rtMRI.avi -t movie -s noscaling --reconst --report`   
### 2. Visualize PCA results  
When the PCA  calculation finishes, run `trendplotgui` with `readparm` 
option set as `Yes` to read arguments from the just finished `trendmaingui`. 
Set `pcn` as 2 to show the first two components as well as scree plot. To 
visualize results obtained from PCA on movie, TREND will extract time of 
frames and use it as ticks in X-axis. If not specified, the default units 
will be seconds.  
To do this at the  command line, use `trendplot.exe -r -e -n 2`   
![trendplot](https://bytebucket.org/chia_hsu/trend/raw/6f17d3f8ebc22cb203e0266265299f6ae1debbd1/docs/png/png_tutorial/2_trendplot.png?token=2a270d122b9c3b7fce157daf06d70ee6a85ef0e7)  
When `trendplotgui` finishes, PC1 and PC2 are plotted. It is clear that 
PC1 represents time course of two breaths and that PC2 tracks the cardiac 
osciallation between diastole and systole.  
![PC1and2](https://bytebucket.org/chia_hsu/trend/raw/6f17d3f8ebc22cb203e0266265299f6ae1debbd1/docs/png/png_tutorial/3_2PCs.png?token=3a61ee2abf72217a3b420464512df1cc982057d2)  
![scree](https://bytebucket.org/chia_hsu/trend/raw/dab91cf79d3c63afc2adba946d3fd894f0b054ae/docs/png/png_tutorial/4_scree.png?token=fa5380d3615f324e1be0f8d2aa9e611fa46e5cd6)  
From the scree plot we can find that PC1 and PC2 contribute to ~50% of 
the total variance.  
### 3. Reconstructing Movies from only PC1 and PC2
It will be interesting to see movies reconstructed by PC1 and PC2. Run 
`trendreconstructgui` and use the following settings.   
![reconstPC1](https://bytebucket.org/chia_hsu/trend/raw/0ab9f8c2be102fcf49fd03bd4bc1fe3eb5be4aa0/docs/png/png_tutorial/5_trendreconstruct_pc1.png?token=c2d8e69da0e6a032c9ced71a5d9ee85dd8fb4de4)  
Leaving most settings at the default. Set the `prefix for the output` to 
`PC1`. It can be seen that a `PC1.mp4` is generated once `trendreconstructgui` 
finishes.  
The command line usage is: `trendreconstruct.exe -r -n 1 -e -o PC1`  
A movie clip `PC2.mp4` reconstructed from PC2 is generated in the same way:  
![reconstPC2](https://bytebucket.org/chia_hsu/trend/raw/0c1f26d1e1424ee0bed0ec096dce1477fffdff56/docs/png/png_tutorial/6_trendreconstruct_pc2.png?token=36c09275ae40dd810c2204a1ba986846c18e3273)  
Its command line usage is: `trendreconstruct.exe -r -n 2 -e -o PC2`  
The two reconstructed movies to result are `PC1.mp4` and `PC2.mp4`. Playing 
the PC1 movie shows only respiration. Playing the PC2 movie shows only the 
heart beating.   
![PC1_breathing](https://bytebucket.org/chia_hsu/trend/raw/4fe917ccc0438956dc51fbd83b603c0a449d3a3b/docs/png/png_tutorial/PC1.gif?token=d9ba88d8458d8675b997e4dce2133b9ada145c5e)   
Above is `PC1.mp4`  
![PC2_cardiac](https://bytebucket.org/chia_hsu/trend/raw/4fe917ccc0438956dc51fbd83b603c0a449d3a3b/docs/png/png_tutorial/PC2.gif?token=1564c52a5c0c7ca632c606b72e8f56bf170d1a11)  
Above is `PC2.mp4`  
