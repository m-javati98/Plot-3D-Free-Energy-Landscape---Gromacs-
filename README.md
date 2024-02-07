# 3D-plot-Free-Energy-Landscape
**1**-Calculate covariance matrix and calculate the eigenvectors and eigenvalues.\
gmx covar -s md.gro -f mdfit.xtc -o eigenvalues.xvg -v eigenvectors.trr -xpma covapic.xpm\
**2**-Calculate PC1 and PC2.\
gmx anaeig -f md.xtc -s md.gro -v eigenvectors.trr -last 1 -proj pc1.xvg\
gmx anaeig -f md.xtc -s md.gro -v eigenvectors.trr -frist 2 -last 2 -proj pc2.xvg\
**3**-Concatenate PC1 and PC2 in one file.\
paste pc1.xvg pc2.xvg  | awk '{print $1, $2, $4}' > PC1PC2.xvg\
**4**-Calculate Gibbs Free Energy.\
gmx sham -f PC1PC2.xvg -ls FES.xpm\
**5**-Use Python Script https://github.com/jobinjobzz/FEL_3D-map-generation-script/blob/main/xpm2txt.py to Convert XPM to TXT.\
**6**-Save Python Script in .py format and upload it into Directory.\
**7**-Install Python Version2 (!apt-get install python2).\
**8**-Run the Script USING (!python2 xpm2txt.py -f $.xpm -o $.txt) Replace <$> by desired name.\
**fel.txt is a sample of an output file of the Python script**.\
**9**-Use TXT output of step 5 as input to got the below 3D rotatable Free Energy Landscape.\
![newplot](https://github.com/m-javati98/3D-plot-Free-Energy-Landscape/assets/119846271/87440a47-272b-46fe-bd92-b8db39be1fb4)
