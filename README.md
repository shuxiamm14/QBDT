# QBDT
a new Boosting Decision Tree method with Systematical Uncertainties into training for High Energy Physics

# Reference
see https://arxiv.org/abs/1810.08387

# Example 
An example in High Energy Physics, Higgs -> tau tau gamma, under the directory tautaugamma

# Description of the files
- qbdtmodule.py : define QBDT class (you do not need to touch it)
- runbdt.py : perform training
- testbdt.py : test and show performance

# First try without systematics:
- run training: python runbdt.py trees0 0 0 10
- run testing: python testbdt.py trees0 
- I put the training and testing results in trees0/example/. You can have a comparison.


# First try with ONE systematic source:
- run training: python runbdt.py trees1 1 1 10
- run testing: python testbdt.py trees1 1 
- I put the training and testing results in trees1/example/. You can have a comparison.


# How to run training?
- command format: python runbdt.py dir Nsysts Switch Ntrees # see the explanation below
- dir: directory for storing training results
- Nsysts: number of systematics 
- Switch: a boolean flag to switch on systematics or not in training. If Nsysts==0, Switch will be always 0.
- Ntrees: number of trees used for training, 100 by default if not specified.

# How to test and show performance?
- command format: python testbdt.py dir Nsysts Ntrees # see the explanation below
- dir: directory for storing training results
- Nsysts: number of systematics, 0 by default if not specified
- Ntrees: number of trees used for testing, 100 by default if not specified.


# Warning
- We have to add a branch in the root file to tell the algorithm which events are used for training or testing. In the current example, this branch is "tranflag". It is generally randomly and unformed from 0 to 1. Events with "trainflag<0.5" are used for training while the others used for testing. I will try to split the events automatically in the future.

# To-do
- Add a function to split events for training and testing automatically.
- Try to improve the training speed. I find python is slow. Maybe I should consider rewritting using C++.

