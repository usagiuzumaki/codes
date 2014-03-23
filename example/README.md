README
======

Here we present several exemplar command lines to use rvtests.
A complete manual can be found: 
[https://zhanxw.github.io/rvtests/](https://zhanxw.github.io/rvtests/)

= run single variant test perform wald test

    ../executable/rvtest --pheno pheno --inVcf example.vcf --single wald --out out1


= using the second column of phenotype

    ../executable/rvtest --pheno pheno --inVcf example.vcf --single wald --mpheno 2 --out out2


= using the phenotype y2

    ../executable/rvtest --pheno pheno --inVcf example.vcf --single wald --pheno-name y2 --out out3


= use covariate c1,c2

    ../executable/rvtest --pheno pheno --inVcf example.vcf --single wald --covar covar --covar-name c1,c2 --out out4

= use covariate file with missing data

    ../executable/rvtest --pheno pheno --inVcf example.vcf --single wald --covar covar.missing --covar-name c1,c2 --out out5

= produce meta-analysis statistics for unrelated individuals, using covariates, regress covariates on pheontpye, then inverse normalize residuals, perform score test and generate covariance matrices

    ../executable/rvtest --pheno pheno --inVcf example.vcf --meta score,cov --covar covar --covar-name c1,c2 --useResidualAsPhenotype --inverseNormal --out out6

= generate kinship matrix from pedigree

    ../executable/vcf2kinship --ped pheno --bn --out output

= generate empirical kinship matrix from VCF file using Balding-Nicols method

    ../executable/vcf2kinship --inVcf example.vcf --bn --out output

= produce meta-analysis statistics for related individuals, using covariates, regress covariates on pheontpye, then inverse normalize residuals, perform score test and generate covariance matrices

need to use a kinship matrix (see previous steps) output.kinship
then, use:

    ../executable/rvtest --pheno pheno --inVcf example.vcf --meta score,cov --covar covar --covar-name c1,c2 --useResidualAsPhenotype --inverseNormal --kinship output.kinship --out out7


= produce meta-analysis statistics under dominant and recessive model for unrelated individuals, using covariates (c1, c2 columns in covar) and phenotype (y4 column in pheno)

    ../executable/rvtest --pheno pheno --inVcf example.vcf --meta score,cov,dominant,recessive --covar covar --covar-name c1,c2 --out out8 --pheno-name y4