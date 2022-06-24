# List of Differentially Private methods for Synthetic Data Generation

## GAN-based methods

### Methods that are designed to be differentially private

#### DPGAN (2018)
This is the first work on differentially private GANs. There is however 
no formal proof of preserving differential privacy (e.g. see issues in Github link).
No privacy budget accountant is introduced.

https://arxiv.org/pdf/1802.06739.pdf

https://github.com/illidanlab/dpgan

#### DPWGAN (NIST 2018)
This is a method proposed for NIST competition (ranked fourth in that competition).
This method is following DP-SGD recipe closely and is reliable. Also, most of the subsequent
works use this implementation as the benchmark for DP GANs.


https://github.com/nesl/nist_differential_privacy_synthetic_data_challenge


#### DPCGAN (CPVR-workshop 2019)
This work focuses on conditional GAN. They use RDP accountant (this is different from 
original DP-SGD accountant). However, this is a workshop paper and 
I could not find a formal computation, only a description of the algorithm is given. 


https://arxiv.org/pdf/2001.09700.pdf

https://github.com/reihaneh-torkzadehmahani/DP-CGAN

RDP: Mironov, Ilya. "Rényi differential privacy." 2017 IEEE 30th computer security foundations symposium (CSF). IEEE, 2017.

#### GS-WGAN (Neurips 2020)
Gradient-sanitized Wasserstein Generative Adversarial Networks.
Instead of sanitizing gradients of discriminator, 
they sanitize generator directly. They consider RDP.

https://proceedings.neurips.cc/paper/2020/file/9547ad6b651e2087bac67651aa92cd0d-Paper.pdf

https://github.com/DingfanChen/GS-WGAN

#### HealthGAN (2020)

This work focuses on healthcare domain, and does not enforce 
differential privacy (has a different measure for privacy).

https://link.springer.com/chapter/10.1007/978-3-030-61146-0_26

https://github.com/TheRensselaerIDEA/synthetic_data

#### DTGAN (ACML 2021)

This is the main paper of the following PhD dissertation. 
I could not find an implementation for this. 

Paper: https://arxiv.org/pdf/2107.02521.pdf

Dissertation: https://arxiv.org/pdf/2108.10064.pdf

#### PEARL (ICLR 2022):  
Data Synthesis via Private Embeddings and Adversarial Reconstruction Learning.
A new method for privacy guarantee is developed which does not use
DP-SGD or PATE. It may or may not use a critic in the setup. 
The code could not be found.

https://openreview.net/forum?id=M6M8BEmd6dq


#### PATEGAN (ICLR 2019)
A PATE based method (as opposed to DP-SGD). Trains k teachers, add noise to aggregation of these teachers and
use the noisy output to train a student which will be used to train
generator.

https://openreview.net/pdf?id=S1zk9iRqF7

https://github.com/vanderschaarlab/mlforhealthlabpub/tree/main/alg/pategan

#### G-PATE (Neurips 2021)
Similar to GS-WGAN trains the discriminator non-privately while only training 
the generator with DP guarantee, and both sanitized gradients that the generator 
received from the discriminator.

https://arxiv.org/pdf/1906.09338.pdf

https://github.com/AI-secure/G-PATE

#### DPSGD vs PATE (2021)
The following two works compare how different private models affect disparate impact.
This can be a noteworthy point when choosing a method synthetic data generation.

https://arxiv.org/pdf/2111.13617.pdf

https://arxiv.org/abs/2109.11429

### Methods that can be made differentially private

Here I list some of the relevant methods for data generation that are not 
differentially private by design, but can be made so with some modifications.
I will also point out the main advantages of each of the methods. 

#### CTGAN
Specifically designed to handle tabular data.

https://arxiv.org/abs/1907.00503

https://github.com/sdv-dev/CTGAN

#### medGAN
Uses an autoencoder in the architecture to handle discrete variables.

https://arxiv.org/abs/1703.06490

https://github.com/mp2893/medgan

#### DECAF (Neurips 2021)
This work has two aspects that might be interesting: 
1- The generation mechanism is causally aware 
2- If we have concerns about fairness we can impose
of the fairness notions

https://openreview.net/forum?id=XN1M27T6uux

https://github.com/vanderschaarlab/DECAF

## Other methods

#### PrivBayes (2017)

https://dl.acm.org/doi/pdf/10.1145/3134428

https://github.com/DataResponsibly/DataSynthesizer
#### PriView (2014)

https://dl.acm.org/doi/pdf/10.1145/2588555.2588575

#### PGM (ICML 2019)
Graphical-model based estimation and inference for differential privacy
Won the NIST competition in 2019. 


https://arxiv.org/pdf/1901.09136.pdf

https://github.com/ryan112358/private-pgm

#### PrivSyn (2021)
PrivSyn: Differentially Private Data Synthesis

No code found, claim that it can handle large tabular datasets:
In this paper, we present PrivSyn, the first automatic synthetic 
data generation method that can handle general tabular datasets 
(with 100 attributes and domain size > 2^500).

They want to find a distribution that satisfies noisy marginals.
They also pick some joint marginals (part of their novelty is 
the way they choose pairs), and produce some samples to match the
noisy distribution. They "massage" the produced samples to satisfy
constraints more accurately in via a post-processing step.


https://www.usenix.org/system/files/sec21fall-zhang-zhikun.pdf

#### DP-MERF (AISTAT 2021)

Differentially-private mean embeddings with random features.
They train a generative model by minimize an approximation of MMD
(between true data and generated samples). They also specialize their 
method for heterogeneous and imbalanced data.


http://proceedings.mlr.press/v130/harder21a/harder21a.pdf

https://github.com/ParkLabML/DP-MERF
