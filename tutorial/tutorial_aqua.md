## Tutorial: The Kinetics of Aqutaion of trans-[Co(en)<sub>2</sub>Cl<sub>2</sub>]<sup>+</sup>
### Introduction  
- [JCAMP-DX](http://www.jcamp-dx.org) is an internationally accepted format 
that is suitable for spectra collected from various spectroscopy instruments. 
JCAMP-DX can be used to store a series of spectra using its multi **BLOCKS**   
- Here is a simple example of analyzing kinetics of aquation of trans-[Co(en)
<sub>2</sub>Cl<sub>2</sub>]<sup>+</sup> from a single JCAMP-DX 
[file](http://wwwchem.uwimona.edu.jm:1104/spectra/testdata/blckpac1.jdx), 
which includes a series Vis spectra using 5 data blocks  
- More examples of JCAMP-DX data can be found in [http://wwwchem.uwimona.edu.jm:1104/spectra/testdata/index.html](http://wwwchem.uwimona.edu.jm:1104/spectra/testdata/index.html)
- Basic information of the experiments can be found in the header of the 
downloaded [`blckpac1.jdx`](http://wwwchem.uwimona.edu.jm:1104/spectra/testdata/blckpac1.jdx) file.  
```bash
##TITLE= Aquation of trans-[Co(en)2Cl2]+
##DATA TYPE= LINK
##BLOCKS= 5
##ORIGIN= Dept of Chem, UWI, Mona, JAMAICA
##OWNER= public domain
##TITLE= (t1) Aquation of trans-[Co(en)2Cl2]+
##JCAMP-DX= 4.24
##DATA TYPE= UV/VIS SPECTRUM
##BLOCK_ID=1
##ORIGIN= Dept of Chem, UWI, Mona, JAMAICA $$Exported PE UV WinLab Data File
##OWNER= public domain
##DATE= 96/11/04
##TIME= 18:07:10.00
##SPECTROMETER/DATA SYSTEM= PERKIN-ELMER LAMBDA 19 UV/VIS/NIR UV
```  

- The Vis spectra series can be visualized as:   
<img src="../png/Vis.jpg" width="600px" alt="Vis Spectra">



### Steps
#### 1. Prepare `xaxisfile` by extracting time information from all blocks (Optional)  
- The aquation of trans-[Co(en)<sub>2</sub>Cl<sub>2</sub>]<sup>+</sup> is 
a time-dependent reaction. The experiment time of each block was shown 
by the `##TIME` flag, such as  
```bash
##TIME= 18:07:10.00
```   

- Although TREND does not need time information to perform PCA analysis on 
this kinetic experiment, it will be helpful to visualize the time-course 
of reaction by plotting principal components vs time.  
- Currently the `x axis` points in `xaxisfile` must be integer or floating point numbers, 
therefore the time format must be converted.  
- 1.1. Extract time information  
	I. This can be done manually or running the following command in Linux or macOS terminal  
	```bash
	cat blckpac1.jdx |grep "TIME"|awk '{print $2}' > time.txt
	```  

	II. Then the `time.txt` contains the following lines:  
	```bash
	18:07:10.00
	18:07:33.00
	18:08:07.00
	18:08:40.00
	18:09:14.00
	```  

- 1.2. Convert `time.txt` to `xaxisfile`  
	I. Open `time.txt` using `Excel` or `OpenOffice`  
	II. Convert time to seconds in `Excel`  
	The time format in the A column is `hh:mm:ss.ff`, the simplest way 
	is to convert time to second  
	Then column B is time with the unit of second
<img src="../png/excel1.png" alt="excel1" width="600px">  

	III. Calculate time change as difference between each time 
	point to the first time point
<img src="../png/excel2.png" alt="excel1" width="300px">  
	IV. Now save the column C to a file `x-axis.txt`, which will be used as 
	`xaxisfile` for `trendmain` or `trendplot`  
	```bash  
	0.00
	23.00
	57.00
	90.00
	124.00
	```  

#### 2. Do PCA on the multi-block JCAMP-DX file  
	2.1 First launch `trendmaingui`, and specify options according to the image  
<img src="../png/tutorial_aqua/2.png" alt="trendmaingui" width="600px">  
	2.2 Press start button, TREND will run and finish soon   
<img src="../png/tutorial_aqua/1.png" alt="trendmaingui" width="600px">  
	2.3 After `trendmain` finishes, an HTML named as `Aquation-report.html` is generated. 
<img src="../png/tutorial_aqua/report.png" alt="trendmaingui" width="800px">  

Note TREND does not support reconstruction of JCAMP-DX now.  
