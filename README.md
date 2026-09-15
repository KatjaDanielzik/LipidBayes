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

i: observation (i.e. one lipid abundance in one subject in one biological condition)   
c: lipid sub-class   
cond: experimental condition (i.e. normal or tumor)   
l: lipid   
s: subject   
sat: chain saturation category (MUFA, PUFA, saturated)   
len: chain length category (middle, long, very long)

```math
\begin{equation}
\begin{aligned}
\mathrm{y}_{i} &\sim {\sf normal}(\mu_i,\sigma_{\ell,cond}) \\
\mu_i &= \alpha^{\mathrm{subject}}_{s(i)} + \alpha^{\mathrm{lipid}}_{\ell(i)}
      + \mathrm{cond}_i \,\delta^{\mathrm{lipid}}_{\ell(i)} \\
\delta^{\mathrm{lipid}}_{\ell} &= \delta^{\mathrm{cond}} + \beta^{\mathrm{class}}_{c(l)} +
\beta^{\mathrm{satClass}}_{c(l),sat(l)} + \beta^{\mathrm{lenClass}}_{c(l),len(l)} +
\upsilon_{\ell} \\
\end{aligned}
\end{equation}
```


partial pooling
```{=latex}
\begin{equation}
\begin{aligned}
\beta^{\mathrm{satClass}}_{c,sat} &\sim{\sf normal}(\mu^{sat},\sigma^{sat}) \\
\beta^{\mathrm{lenClass}}_{c,len} &\sim{\sf normal}(\mu^{len},\sigma^{len}) \\
\sigma_{\ell,\mathrm{cond}} &\sim {\sf exponential}(\lambda_{c,cond}) \\
\end{aligned}
\end{equation}
```

priors
```{=latex}
\begin{equation}
\begin{aligned}
\alpha^{\mathrm{subject}}_{s} &\sim {\sf normal}(0,1) \\
\alpha^{\mathrm{lipid}}_{\ell} &\sim {\sf normal}(0,1) \\
\beta^{\mathrm{class}}_{c} &\sim {\sf normal}(0,1) \\
\beta^{\mathrm{sat}}_{k} &\sim {\sf normal}(0,1) \\
\beta^{\mathrm{len}}_{j} &\sim {\sf normal}(0,1) \\
\upsilon_{\ell} &\sim {\sf normal}(0,1) \\
\mu^{sat} &\sim {\sf normal}(0,1) \\
\mu^{len} &\sim {\sf normal}(0,1) \\
\sigma^{sat} &\sim {\sf exponential}(1) \\
\sigma^{len} &\sim {\sf exponential}(1) \\
\lambda_{c,cond} &\sim {\sf exponential}(1) \\
\end{aligned}
\end{equation}
```
