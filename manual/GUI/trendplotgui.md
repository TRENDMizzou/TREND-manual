### Trendplot -- display the principal components identified by the main script
- The program for plotting with GUI is `trendplotgui.exe` in Windows and 
Linux, or `trendplotgui.app` ini OS X. The `report` option of the main 
script generates an HTML report including several figures including the 
first 3 PCs and scree plot, `trendplotgui` non-essential for visualizaing 
results. However, `trendplotgui.exe` provides more control of plotting, 
 such as choices of kinds of normalization and single components to plot.   
- Note everytime when `trendmaingui` launches it creates a temp directory to
to save temporary files for `trendplotgui` and `trendreconstructgui` and 
deletes the old one (if it exists). Therefore, `trendplotgui` and 
`trendreconstructgui` processes are based on the last run of `trendmaingui`.   
<img src="https://bytebucket.org/chia_hsu/trend/raw/72cf7b768324cb6311286619394581b4eea5558f/docs/png/png_gui/Png5_trendplotPCA.png?token=f6e6435856eb1c05bd6911f218319fbd00ef99f1" width="600" alt="pca">  
- There are two modes `trendplotgui`: PCA and ICA.. It is critical to select 
the appropriate mode.  
- **`pca`** mode: The V<sup>T</sup> matrix and S matrix are needed for plotting PCA results. 
These matrices can be selected using the `vtmatrix` and `smatrix` file 
choosers. However, there is an easier way: Setting `readparm` to `Yes` 
will read the arguments that `trendmain` used and automatically locate 
the matrices as well as the choices of `xaxis` and `xunit`. `pcn` sets 
the first N PCs to be plotted. When the `single` checkbox is turned on, 
`pcn` just plot the N<sup>th</sup> PC. The type of normalization can be selected by 
setting `normalmode` according to Table 1 of the [manual](./manual.md).  
- **`ica`** mode is very similar to **`pca`** mode, but does not read `smatrix` 
or show a scree plot.  
]<img src="https://bytebucket.org/chia_hsu/trend/raw/72cf7b768324cb6311286619394581b4eea5558f/docs/png/png_gui/Png6_trendplot_ICA.png?token=b40217c3228e0dd9440e68fd9c610bd1a42980cd" alt="ica" width="600">   
