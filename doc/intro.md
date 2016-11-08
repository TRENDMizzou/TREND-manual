# TREND: TRack Equilibrium or Non-equilibrium shifts in Data

### Resolve and Reconstruct Trends such as Binding Isotherms and Time Courses Directly from Spectra, Imaging, or Lists

## Introduction:

TREND is a software package that determines the main trend\(s\) of change across a series of 2D digital measurements, such as imaging and NMR spectra. TREND works by applying principal component analysis to non-interpreted 2D digital measurements in multiple formats including spectra \(from NMR, other spectroscopies, and mass spectrometry\), raw NMR data, movies, images, lists, and spreadsheet files. The principal components extracted from them by TREND represent the main changes among the data frames. These could be binding isotherms, time courses, or a variety of population shifts. The main requirement is that the data frames be measured consistently in order to allow quantitative comparison. Series of 2D measurements in an unsupported format may be converted into a text file or spreadsheet in order to be read by TREND for analysis. The TREND package includes a program to reconstruct movies or a stack of spectra from the principal components selected by the user. TREND has been developed for ease of installation under Windows, Mac OS X, and Ubuntu and Fedora versions of Linux. TREND \(copyright pending and sponsored by NSF\) is free for academic users.

![TREND introduction](https://bytebucket.org/chia_hsu/trend/raw/303d974a4e9aea9820459ff9adf024973fd3b86a/docs/png/png_readme/Picture1.png?token=75e14157952a262d5b24a87796b83cd83ec9c991)

### Simple Example: Determine binding isotherm from NMR spectra in UCSF format

#### _GUI USAGE_

1. Choose `nmr` tab of `trendmaingui` and press browse button highlighted by the box.  
  ![NMR upper](https://bytebucket.org/chia_hsu/trend/raw/10b9c98b57798b4d9d157e603bdbfab66f27825b/docs/png/png_readme/Picture2.png?token=03b7da06db65da6849628a2c8d8c79b26383b1f9)  
  Choose a series of Sparky format spectra \(.UCSF files\) and TREND will 
  sort them numerically.  
  ![File read](https://bytebucket.org/chia_hsu/trend/raw/10b9c98b57798b4d9d157e603bdbfab66f27825b/docs/png/png_readme/Picture3.png?token=6060648d1e97b3faa2892522b38c05eb235f69c3)  
2. Specify required arguments including file format, method of scaling 
  rows, the prefix of output files, threshold for smallest signals to be 
  retained \(x-fold the noise\), whether to export CSV-format spreadsheet 
  files, and whether to generate an HTML report. The default settings are 
  recommended.  
3. Optional arguments are highlighted within the box with dashed line. 
  See the manual for details. Here we specify `xaxis` and `xunits`  
  ![NMR lower](https://bytebucket.org/chia_hsu/trend/raw/10b9c98b57798b4d9d157e603bdbfab66f27825b/docs/png/png_readme/Picture4.png?token=7b3bdf2976e64a4d939079db4d73e04ff97f2cf4)  
4. Press start button, TREND will run for a while and finish.  
  ![finish GUI](https://bytebucket.org/chia_hsu/trend/raw/10b9c98b57798b4d9d157e603bdbfab66f27825b/docs/png/png_readme/Picture5.png?token=367c41b42077367476e0984addf65561afaeef6b)  
5. After trendmain finishes, an HTML report is generated. It includes the 
  arguments just used, scree plots, PC plots, etc. Please see manual for details.

  ![HtmlScreenShot](https://bytebucket.org/chia_hsu/trend/raw/10b9c98b57798b4d9d157e603bdbfab66f27825b/docs/png/png_readme/Picture6.png?token=d213db826d88cb2b4d4a7da2362bce8347c6dfec)

  #### _Corresponding shell command_

  `trendmain.exe -f file.index -t ucsf -s auto -o example -r auto --report`

  ## Citation

  If TREND is used in your research, please cite the references 
  \[Jia Xu and Steven R. Van Doren, Binding Isotherms and Time Courses Read
  ily from Magnetic Resonance. _Anal. Chem._ 2016, 88 \(16\), pp 8172-8178\]\(
  [http:\/\/pubs.acs.org\/doi\/abs\/10.1021\/acs.analchem.6b01918](http://pubs.acs.org/doi/abs/10.1021/acs.analchem.6b01918)\)


Jia Xu and Steven R. Van Doren, Tracking Equilibrium and Non-equilibrium 
Shifts in Data with TREND. Submitted.

