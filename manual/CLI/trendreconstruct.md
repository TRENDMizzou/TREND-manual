### Reconstruction script - Use the PCA results from the Main script to model the 2D measurements

* #### GUI and CLI programs

  GUI: `trendreconstructgui.exe` in Windows and Linux, `trendreconstructgui.app`
  in OS X

  CLI: `trendreconstruct.exe` in all platforms

* #### Synopsis

  ```
  trendreconstruct.exe -n [components] -m [1/2/3/4]] [-e] [-p] [-r] [-z] 
  [-d] [--rmsd] [--gif] [--dpi integral for dpi of output PNG files]
  ```

* #### Description

  - `trendreconstruct.exe` rebuilds the original 2D measurements using the first
     N principal components requested by the user. The script `trendreconstruct.exe` 
	 requires that `trendmain.exe` first be run with the `--reconstruct` 
	 option turned on. Normally 
     `trendmain.exe` will not save the files needed for PCA reconstruction unless
     the  `--reconst` option is used.
  - Note that each time when `trendmaingui` or `trendmain` launches it creates 
  a temp directory to save temporary files for `trendplot` and `trendreconstruct` and 
deletes the old one (if it exists). This prepares 
`trendreconstruct` to use the last run of `trendmain` or `trendmaingui` 
performed with the `--reconstruct` option turned on.   

* #### Options

  * `-n component(s) selected for reconstruction`  
    `-n` specifies principal components selected to use in rebuilding 
    the original measurements. For example, `-n 1` means reconstruct the 2D 
    measurements using only the first component, while `-n 3` uses the 
    third component. To reconstruct individual, non-consecutive components, 
    you can separate the page numbers with commas: e.g. `-n 2,4,6` would 
    reconstruct using the second, fourth, and sixth components. To reconstruct 
    the range of components 1 to 3, use `-n 1-3`. Range and individual 
    components can be selected together, e.g. `-n 1,3-5,7` means reconstruction 
    by components 1, 3, 4, 5, 7. Note space is **not** allowed between selected 
    components unless quotation marks are used. i.e. `-n '1, 3-5, 7'`.   
  * `-m [1/2/3/4]`

    Background:  `trendmain.exe` reorganizes the measurements listed in 
    `file.index` as a large 2D matrix, filters them, and scales them for PCA. 
    The `-m` option specifies which stage of the process should be reconstructed. 
    `-m` specifies which matrix will be reconstructed. The choices are:  
    
| matrix mode | meaning |
| -- | -- |
| 1 | This recovers the state right before doing PCA. The large 2D matrix is row (column) scaled, with unchanged rows and noisy regions filtered out |
| 2 | This differs from matrix mode 1 in that the rows (columns) are unscaled |
| 3 | This option also recovers the filtered, unchanged rows from matrix mode 2 |
| 4* | This option differs from matrix mode 3 in also recovering the low intensity regions filtered out from being below the threshold |
\* mode 4 is for **Fourier-Transformed 2D NMR spectra** where `-r` option 
    was used in `trendmain.exe` to set the threshold for filtering low intensity
    regions.

  * `-e`

    `-e` is optional. When it is on, the reconstructions of the measurements are
    exported in the same format as the original measurements read into 
    `trendmain.exe`. If input format is `movie` or `png`, the output 
    format will be mp4 format movie clip. mp4 movie reconstructed from `movie` 
    shares the same time length as the input movie. mp4 movie reconstructed 
    from a series of PNG images is set as 10 second long.

  * `-p`

    `-p` is optional. When it is on, the reconstructed images are exported as 
    images in PNG format.

  * `--gif`  
    `--gif` is optional. When it is on, the reconstructed movies are 
    exported as GIF animation just in case there is no appropriate 
    media player to play `.mp4` movie clip generated by `-e`. GIF animation 
    is more compatible since most web browsers can play it, although it 
    has larger size than mp4.  
  * `--dpi`  
    When `-p` option is turned on, `--dpi` specifies the dots-per-inch resolution
    of the png files to be reconstructed. By default, this is set to 96. This 
    option is not required.  
  * `-z`   
    `-z` option is used to recover rows that do not change and hence was filtered
    out before doing PCA.  
  * `-r`  
    `-r` is used only when reconstructing 2D Fourier-transformed NMR spectra. 
    When doing PCA on 2D NMR spectra, a threshold can be set to filter out noisy
    regions using the `-r` option for `trendmain.exe`. The `-r` option can be 
    used in reconstruction to recover those noisy regions in order to fully 
    recover the original spectra. It is not required and is usually not necessary.  
  * `-d` or `--diff`    
    `-d` turns on the `diff` mode, exporting difference spectra instead of 
    reconstructed spectra. It is used to visualize the difference between original
    and reconstructed spectra.  
  * `--rmsd`  
    `--rmsd` calculates the RMSD between the reconstructed and original data for
    all principal components. A file with suffix name as `-rmsd.txt` and prefix
    name specified by the `-o` option of `trendmain.exe` will be stored. For 
    example, if `trendmain.exe` was used with the `-o example` option, `--rmsd` 
    option generates a file named as `prefix-rmsd.txt`.  
  * `-o [output prefix name]`  
    `-o` specifies the prefix of reconstructed files or images  