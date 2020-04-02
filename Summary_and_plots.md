# Norway
```bash
bgzip -c Norway_new.vcf > Norway_new.vcf.gz
vcftools --gzvcf Norway_new.vcf.gz --chr 1 --chr 2 --chr 3 --chr 4 --chr 5 --chr 6 --chr 7 --chr 8 --chr 9 --chr 10 --chr 11 --chr 12 --chr 13 --chr 14 --chr 15 --chr 16 --chr 17 --chr 18 --chr 19 --chr 20 --chr 21 --chr 22 --chr 23 --chr 24 --chr 25 --chr 26 --chr 27 --chr 28 --chr 29  --recode --out Norway_subset_chr1-29

vcftools --vcf Norway_subset_chr1-29.recode.vcf --plink --out Norway

plink --file  Norway --recode transpose --out  Norway --chr-set 29

plink --tfile Norway --out Norway --chr-set 29

plink --file Norway --geno 0.01 --recode --out Norway_99 --chr-set 29

# 7996578 variants removed due to missing genotype data (--geno).
# 30297 variants and 6 samples pass filters and QC.

plink --file Norway_99 --freq --out Norway_99 --chr-set 29

plink --file Norway_99 --maf 0.01 --recode --out Norway_99_001 --chr-set 29
# 29637 variants and 6 samples pass filters and QC.

# To sort stuff
sort -rnk5 Norway_99.frq|head -1

plink --chr-set 29 --file Norway_99_001 --genome --out Norway_99_001

head Norway_99_001.genome

sort -nk10 Norway_99_001.genome | tail

plink --chr-set 29  --file Norway_99_001 --mds-plot 4 --cluster --out Norway_99_001
# To create plots in R
R
A1=read.table("Norway_99_001.mds", header=T)
pdf("rplot.pdf")
plot(A1$C1, A1$C2)
q()
y
# To download the plot in .pdf format
scp gstud01@10.44.152.8:/home/gstud01/Variants_trial/rplot.pdf /Users/kalilamali/Desktop/rplots.pdf
```

# USA
```bash
bgzip -c USA_new.vcf > USA_new.vcf.gz

vcftools --gzvcf USA_new.vcf.gz --chr 1 --chr 2 --chr 3 --chr 4 --chr 5 --chr 6 --chr 7 --chr 8 --chr 9 --chr 10 --chr 11 --chr 12 --chr 13 --chr 14 --chr 15 --chr 16 --chr 17 --chr 18 --chr 19 --chr 20 --chr 21 --chr 22 --chr 23 --chr 24 --chr 25 --chr 26 --chr 27 --chr 28 --chr 29  --recode --out USA_subset_chr1-29

vcftools --vcf USA_subset_chr1-29.recode.vcf --plink --out USA

plink --file  USA --recode transpose --out  USA --chr-set 29

plink --tfile USA --out USA --chr-set 29

plink --file USA --geno 0.01 --recode --out USA_99 --chr-set 29

#10049350 variants removed due to missing genotype data (--geno).
#461441 variants and 6 samples pass filters and QC.

plink --file USA_99 --freq --out USA_99 --chr-set 29

plink --file USA_99 --maf 0.01 --recode --out USA_99_001 --chr-set 29
# 402133 variants and 6 samples pass filters and QC.

# To sort stuff
sort -rnk5 USA_99.frq|head -1

plink --chr-set 29 --file USA_99_001 --genome --out USA_99_001

head USA_99_001.genome

sort -nk10 USA_99_001.genome | tail

plink --chr-set 29  --file USA_99_001 --mds-plot 4 --cluster --out USA_99_001

# To create plots in R
R
A2=read.table("USA_99_001.mds", header=T)
pdf("rplot.pdf")
plot(A2$C1, A2$C2)
q()
y

# To download plots in .pdf format
scp gstud01@10.44.152.8:/home/gstud01/Variants_trial/rplot.pdf /Users/kalilamali/Desktop/rplots.pdf
```
