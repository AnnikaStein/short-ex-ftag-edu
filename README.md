# Flavour-Tagging Short Exercise

Welcome to the Flavour-Tagging Short Exercise held at CMSDAS@CERN 2023!

## Intro
A set of slides with introductory material, definitions, useful links is available at [Indico](https://indico.cern.ch/event/1257234/timetable/#44-short-exercise-4b-flavour-t).
## Setup with SWAN
Connect to https://swan.cern.ch/

If you are a participant of CMSDAS@CERN 2023 for this Short Exercise, chances are all you need to do is to go to pick the default environment (no additional environment script necessary, no paths), choose 10GB memory, and then navigate to Share -> Projects shared with me to find the project called „CERN-CMS-DAS-2023-Short-Ex-FTAG“. Pick this project, it will contain all the relevant notebooks for the exercises.

If you come here independently, no need to worry. Start similar, pick the default environment, choose 10GB memory, click the Console symbol on the top navigation bar ("New terminal") and proceed with these commands:
1. Checkout the exercise repository into new directory (example directory given below for convenience)
```shell
mkdir -p ~/SWAN_projects/Short-Exercises
cd ~/SWAN_projects/Short-Exercises
git clone https://github.com/CERN-CMS-DAS-2023/short-ex-ftag.git
```
2. Start ipython notebooks via SWAN  
You can now go back to the browser tab you started with that holds your SWAN projects. Navigate to the recently cloned directory and open the individual exercises from the `notebooks` folder.

## Alternatively: Setup with lxplus
To start with the exercises, perform these initial steps for the setup at lxplus (e.g. after doing `ssh -l your-lxplus-username lxplus.cern.ch` from your own machine):

1. Get Miniconda (if you have not yet done so in another exercise)
```shell
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```
Special note if you obtained your lxplus computing account rather recently (2021 or later), and don’t have access to an AFS Workspace but only EOS, installation may take a while, therefore we recommend (if possible) to start early with the instructions. You may have to add the following update to the conda configuration:
`conda config --add pkgs_dirs /new_path_pkgs/` (where `/new_path_pkgs` would be somewhere on your /eos directory to not fill your personal AFS user space)
and a similar command once more but for `envs_dirs` and another path on /eos to store the environments. That way your AFS stays clean and operational.

2. Checkout this repository into new directory (example directory given below for convenience)
```shell
mkdir -p ~/private/CMSDAS2023/Short-Exercises
cd ~/private/CMSDAS2023/Short-Exercises
git clone git@github.com:CERN-CMS-DAS-2023/short-ex-ftag.git
```
(_Alternatively, if you don't have your ssh-key connected to github, replace the above URL with `https://github.com/CERN-CMS-DAS-2023/short-ex-ftag.git` in the command_)

3. Install relevant python packages into a conda-environment (comes with the Git repo)
```shell
conda env create -f env.yml
```
4. Connect to a screen session (start jupyter lab server) and open in browser
```shell
screen -S server
```
In that new screen-session, make sure to have the active conda environment:
```shell
conda activate FTAG-Tutorial
```  
and start a jupyter lab server with forwarding to a specific port (choose a random four-digit number, don't all choose the same - the 7890 is just an example!)
```shell
jupyter lab --no-browser --port=7890
```
Note down the lxplus-machine you were working with (most likely, something like lxplus7XY with XY some numbers. Note down the port you have chosen above. Copy-paste the first http-link presented to you after starting the jupyter server instance, this should be opened by you in a new web browser tab on your own machine. In this first ssh connection, you may detach from the screen via `Ctrl + A` (hold `Ctrl`) followed by `Ctrl + D`. One can always go back to this screen-session via `screen -r server`. From a new ssh-terminal (at your own machine!), connect to the port on which you started the server, pick the exact machine you worked with for the previous step:
Example:
```shell
ssh -L 7890:localhost:7890 anstein@lxplus702.cern.ch
```
General case, to be filled by you:
```shell
ssh -L port-you-picked:localhost:port-you-picked your-lxplus-username@lxplusXYZ.cern.ch
```
Now open the http-link from jupyter lab in your browser and navigate to the short exercise. All packages to work with the exercises should be available from there, you don't need to use the terminal from now on, just keep the session open while you're working.

## Tutorials
All individual tutorials / exercises are available from the `notebooks` directory. There are three .ipynb files which are plug-and-play, just (double-)click to open in SWAN (jupyter lab) and follow the instructions inside.

### Inputs, Targets and Tagger Outputs
Explore the inputs which are used to perform jet flavour tagging with some example files. Understand what the machine learning algorithms need to predict by investigating the targets, and compare with what the taggers actually do when passing inputs through the networks by looking at the output scores.
### Performance
Learn how network performance is evaluated and which performance metrics play a key role for flavour tagging. Perform more studies to evaluate performance as a function of certain parameters and compare across samples.
### Bonus
Explore how performance depends on kinematic quantities related to the jet. This is one concept to keep in mind, differential distributions *do* matter (not only inclusive metrics), in this case explored for simple features like pseudorapidity and transverse momentum. Most likely you will also need to adapt to differentially measured scale factors (in bins of disciminators, though) when using such algorithms in an analysis.
## Contact
**_Annika Stein, 2023_**  
:email: [annika-stein@cern.ch](mailto:annika-stein@cern.ch), :octocat: [@AnnikaStein](https://github.com/AnnikaStein)