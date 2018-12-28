# GREML

## Make Genetic relationship matrix


##### Making a GRM from all SNPs in a family data set
```
./gcta64 --bfile test --make-grm --out test
```
##### Creating an additional GRM from the GRM above (setting the off-diagonals that are < 0.25 to 0)
```
./gcta64 --grm test --make-bK 0.25 --out test_bK    (GCTA document used 0.05, but it is too stringent, especially for small datasets)
```

##### make a text file to include the name of GRM used for analysis (mgrm.txt)
```
test
test_bk
```
## GREML analysis

##### Masculinity
```
./gcta64 --reml --mgrm mgrm.txt --pheno pheno --out test_bKsK
```

##### Finger ratio
```
./gcta64 --reml --mgrm mgrm.txt --pheno finger_ratio --out finger_bKsK
```
