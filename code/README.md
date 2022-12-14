# code

This directory houses all codes and functions used in our study. They are organised among the following R scripts:  
* _Functions.R_: script containing all functions used in the study.
* _Transient simulations_: folder containing the scripts and templates used for the analyses.
* _Tot.data.R_: script used to transform and extend the data generated by the transient dynamics, with further equilibrium analyses, and comparison between resident and invaded communities. See below, for more details.
* _BMR_MeanProp.R_: script to calculate the averaged proportions of invasion outcomes and diversity and stability changes along species body mass gradients
* _Figures.R_: script to generate the main and supplementary figures in our study.


## Transient simulations
This folder contains the codes we used to conduct all transient analyses across all trophic modules, species mass ratios and abiotic conditions. Due to the heavy computational power and storage these simulations required (more than 10 million simulations), we used the storage facility of the [MetaCentrum][linkmeta] to conduct large amounts of simulations in parallel.

The basic elements required for the simulations are the _Functions.R_ script and the appropriate version of _Transient_ R scripts (depending on focused trophic module), which provide an example of the simulations running for a small range of temperature values and a given species mass ratio (equal to 1 in the example). However, we built different **_Template_** folders in order to generate all the required codes for all combinations of body mass ratios and abiotic conditions. This method is very convenient as it is automatised, homogenous across other templates, very fast to produced large amount of scrips, and avoid inadvertently mistakes "made by hand". As an example, it produce 120 scripts (40 scripts of Functions, Bash and Transient) for each of the 16-25 body mass combinations.

### Template folders
Each **_Template_** folder has the same structure.
1. _BMR-Folder-scripts.R_ script generates the "BMRs" folders that will contain all generated bash and R scripts.
2. _Bash_scripts_: to generate the bash scripts that are required to launch the simulations once uploaded on the computational infrastructure. Each Bash script is generated when using _Bash_Scripts_generator.R_, which basically merges the bloc of texts "BS(1-6)" together and implements the script specificities (species mass combination, index of the script, etc.). The remaining bash script extension enables (e.g. "2spAB.sh") to launch all bash scripts at once, once all materials are uplodaded on the server.
3. _R_Scripts_: to generate all R scripts in the "BMRs" folders. _R_Functions_generator.R_ simply copies a version of the _Functions.R_ in all folder, while _R_Scripts_generator.R_ merges the bloc of texts "R(1-6)" together in order to produce the scripts that vary in the temperature range values and species mass ratios.
4. _Data_merge.R_: to merge the different chunks of data together once all the simulations are over and downloaded.  

We notably used the software [Filezilla][linkfile] to upload and download our codes and data on the computation infrastructure, and [VirtualBox][linkvirtual] to access it and launch our simulations.

[linkmeta]: https://metavo.metacentrum.cz/en/index.html
[linkfile]: https://filezilla-project.org/
[linkvirtual]: https://www.virtualbox.org/
