# Classifying tumors by supervised network propagation   
We develop an general algorithmic framework by adapting the Supervised Random Walk (SRW) algorithm (Backstrom and Leskovec, 2010) with a novel loss function designed specifically for cancer subtype classification. The package is called **Network-Based Supervised Stratification (NBS^2)**  
  
![Fig. 1](./images/Figure_1_method.PNG)  
**Fig. 1. Workflow of the Network-Based Supervised Stratification (NBS^2) of cancer subtypes.** NBS^2 takes three input data sets, represented by red arrows: 1) a molecular network where each edge is annotated by a set of features *x*, and each feature is assigned a initial weight *w*; 2) a tumor-by-gene matrix representing the mutation profile of a cohort; and 3) the defined subtype of each tumor. In each iteration, NBC compute an activation score a for each edge (**Eq. 3**), calculate a transition matrix *Q* (**Eq. 2**), perform a random walk (**Eq. 1**), and compute the value of the cost function *J*(*w*) (**Eq. 4**). Training the classifier is conducted iteratively using gradient descent. To minimize *J*(*w*), the algorithm calculates the partial derivative of *J*(*w*) with respect to the edge feature weights *w* using the chain rule (**Eqs. 7-11**), and updates *w* accordingly. Upon convergence, the algorithm outputs the final feature weights *w*, transition matrix *Q* and propagated mutation profiles *P*, which together defines the classification model.  
  
![Fig. 2](./images/Figure_2_simulation.PNG)  
**Fig. 2. Experiments on simulated data.** (**A**) (Upper) Simulated mutation dataset including characteristic genes of two subtypes (gene 1-10) and an Frequently Mutated Gene (FMG) (gene 16). Mutated genes are shown in dark red and non-mutated genes are shown in white. A reduced set of tumors and genes (10 x 20) is shown as an example; the full simulation is (100 ✕ 1000). An edge-by-feature matrix is also used as a input for the supervised random walk. (Middle left) Unsupervised and (middle right) supervised random walk of mutations over a simulated gene interaction network. Shades of red show propagated mutation values for tumor sample #7. (Bottom) Propagated mutation profiles following (left) unsupervised and (right) supervised random walk. (**B, C**) Principal components analysis (PCA) of the full simulation (100✕1000) between (**B**) unsupervised random walk-based tumor stratification and (**C**) supervised random walk-based tumor classification.  
  
**[This is the main package (SRW_v044.py)](./SRW_v044.py).** It contains all the functions for NBS^2  
  
[This file (simulation_100x1000.ipynb)](./simulation_100x1000.ipynb) contains the code for the simulation (**Fig. 2**)  
[This file (data_processing_BRCA.ipynb)](./data_processing_BRCA.ipynb) contains the code for processing PathwayCommons interaction features and Breast Cancer mutation profiles  
[This file (SRW_cookbook_BRCA.ipynb)](./SRW_cookbook_BRCA.ipynb) contains some example code for classifying Breast Cancer samples into four known subtypes   
  
**[This document (equations_v044.ipynb)](./equations_v044.ipynb)** contains equations of the algorithm  
