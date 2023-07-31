# Issues and Fixes for this courses Virtual Machine:

The course is making use of a virtual machine built for a previous course [NGSBioAfrica2022](https://github.com/WCSCourses/NGS_Bio_Africa)         

The following fixes have already been incorporated into the GSBAfrica2023 VM. They are listed here in case of an arising issue. Fixes that arise throughout the course will be added here. 

#### To fix lumpyexpress error:

```
conda create --name thelumpyenv python=2.7

conda activate thelumpyenv

conda install pysam

conda install numpy

cd /home/manager/course_data/structural_variation/data/exercise3/

samtools view -bh -F 1294 ERR1015069.bam | samtools sort -O bam -T ERR1015069.temp -o ERR1015069.discordants.bam

samtools index ERR1015069.discordants.bam 

samtools view -h ERR1015069.bam | extractSplitReads_BwaMem -i stdin | samtools view -b - | samtools sort -O bam -T ERR1015069.temp -o ERR1015069.splitters.bam

samtools index ERR1015069.splitters.bam

lumpyexpress -B ERR1015069.bam -S ERR1015069.splitters.bam -D ERR1015069.discordants.bam -o ERR1015069.vcf

ls
# deactivate the environment when done
conda deactivate

```



#### To install snpdists

```
conda install snp-dists
```

#### To resolve an iqtree error - big thanks to Gebremeskel Mamu Werid for posting this on Vula
```
#1. To uninstall the iqtree package, you can use:  
sudo apt remove iqtree 
# or 
pip uninstall iqtree

#2. update your system: 
sudo apt-get update

#3. install a specific version of iqtree package: 
conda install -c bioconda -c defaults iqtree=1.6.12

#4.  update your system: 
sudo apt-get update

#5. check if you installed the right version of iqtree 
iqtree --version

```

#### To install figtree

```
sudo apt install figtree
# the password is manager
```

#### To install sleuth for module 7:
```
# Begin by running R

R

BiocManager::install()

install.packages(“devtools”)

BiocManager::install(“pachterlab/sleuth”)

# continue with the practical from here
```

#### to install tximportData in R
```
# Begin by running R

R

BiocManager::install("tximportData")

# continue with the practical from here
```



#### To install salmon for mod 8:
```
conda create -n salmon salmon
conda activate salmon

# run your salmon commands

# deactivate the environment when done

conda deactivate
```
