# LipidBayes
Bayesian Inference of Lipid Abundances: Uncovering Global and Lipid Class Specific Changes in Abundance, Chain Length, and Chain Saturation

# Motivation
Jointly answer the following questions:    
1) How do single lipid abundances change between conditions?

2) How do lipid classes change between conditions?

3) How do chain classes (chain length and chain saturation) change between conditions?
   Within lipid classes and globally

4) Are there lipids that behave differently from their class and chain predictions?


# Method
We developed a new Bayesian model to answer the above questions.
Input are z-scores (mean=0,sd=1) on log transformed lipid abundances of the whole
data set (excluding QC samples).
```
