# GREML
Zaitlen et al. 2013 PLoS Genetics proposed a method to estimate pedigree-based and SNP-based h2 simultaneously in one model using family data. The main advantage of this method is that it allows us to estimate SNP-based h2 in family data without having to remove related individuals. The method has now been implemented in GCTA.

## Make Genetic relationship matrix


##### Making a GRM from all SNPs in a family data set 
```
./gcta64 --bfile test.dev.noduplicates --make-grm --out test
                     (Genotype file)              (GRM matrix)
```
##### Creating an additional GRM from the GRM above (setting the off-diagonals that are < 0.25 to 0) (related individuals only)
```
./gcta64 --grm test --make-bK 0.25 --out test_bK    (GCTA document used 0.05, but it is too stringent, especially for small datasets)
           (GRM matrix)               (GRM matrix)
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
