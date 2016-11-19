### Trendreconstruct - Use the PCA calculations to reconstruct features in the sereis of 2D measurements  
`trendreconstructgui.exe` in Windows and Linux or `trendreconstruct.app` 
in OS X is the program with GUI that uses the results from `trendmaingui.exe` 
to reconstruct single or multiple PC representations of the original 
series of 2D measurements. It is quite self-explanatory. The 
[manual](./manual.md) provides more details.  
<img src="https://bytebucket.org/chia_hsu/trend/raw/72cf7b768324cb6311286619394581b4eea5558f/docs/png/png_gui/Png7_trendreconstruct.png?token=36161555615b4cdd12608a876f1e96ea64782cf4" alt="reconstruct" width="600">  
`trendreconstructgui` reads  parameters and results from `trendmain` or 
`trendmaingui`. A PCA calculation must be carried out by `trendmain` with the 
`reconstruction` option turned on. 
`trendmaingui` reads number of components to use in reconstruction by 
entering strings in the `--pcn` text box. The syntax it uses is 
equivalent to specifying pages in a print dialog. For example, `1` means 
reconstruct the 2D measurements using only the first component, while `2` 
uses the second component only. `1, 3-5, 7` means reconstruction by 
components 1, 3, 4, 5, 7.  
When performing reconstruction of a 
PNG image series, choosing to export the `original format` will actually
 generate an `mp4` movie clip. Choosing the `PNG` option instead plots 
 reconstructed images.  

