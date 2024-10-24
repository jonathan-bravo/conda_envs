# Makefile for setting up genslm environment and installing packages

# Variables
CONDA_ACTIVATE = eval "$$(conda shell.bash hook) && conda activate genslm"
PIP_INSTALL = pip install --no-warn-script-location --no-warn-conflict

.PHONY: all setup install_pip

# Default target
all: setup install_pip

# Target to set up the Conda environment
setup:
	@echo "Setting up Conda environment..."
	@conda env create -f genslm.yaml -y
	@echo "Environment setup complete."

# Target to install packages with pip
# @$(CONDA_ACTIVATE) && $(PIP_INSTALL) git+https://github.com/maxzvyagin/transformers
install_pip:
	@echo "Installing pip packages..."
	@$(CONDA_ACTIVATE) && $(PIP_INSTALL) lightning-transformers==0.2.1
	@rm -rf genslm/
	@git clone https://github.com/ramanathanlab/genslm
	@cp setup.cfg genslm/setup.cfg
	@$(CONDA_ACTIVATE) && $(PIP_INSTALL) -e ./genslm/
	@echo "Pip installation complete."

# conda env remove -n genslm -y