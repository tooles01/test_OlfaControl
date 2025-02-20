# MATLAB scripts for plotting/data analysis

**Analyze datafiles (created by running main.py) using the MATLAB scripts found at [OlfaControl_GUI\analysis](https://github.com/tooles01/OlfaControl_GUI/tree/shannon-branch/analysis).**  

Best practice is to download/clone the entire folder, ["analysis/functions"](https://github.com/tooles01/OlfaControl_GUI/tree/shannon-branch/analysis/functions) contains the dependencies for the plotting scripts (they will not run without those functions).

**Note**: When running functions, MATLAB directory must be "...\OlfaControlGUI\analysis"  
(*import_datafile.m* will not run otherwise)  
<br>

## To load data files:
### analysis_get_and_parse_files.m
Gets raw \*.csv datafile and save as \*.mat file.  
#### Description:
- **Loads \*.csv datafile** from *OlfaControl_GUI\result_files\48-line olfa*  
- **Saves raw file** to *OlfaControl_GUI\analysis\data files (raw)*  
- **Parses file**, converts units, creates data structures, etc  
- **Saves parsed file** to *OlfaControl_GUI\analysis\data (.mat files)*  

**Note:** User must enter datafile name (line 57ish)

**More details [here](https://github.com/tooles01/OlfaControl_GUI/blob/shannon-branch/analysis/Documentation/README_analysis_get_and_parse_files.md)**  