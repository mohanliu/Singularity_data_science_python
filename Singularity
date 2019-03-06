BootStrap: docker
From: continuumio/miniconda3

%labels
   Maintainer MohanLiu (mohan@u.northwestern.edu)
   Version v0.0
   
%environment
     conda=/opt/conda/bin/conda
     pip=/opt/conda/bin/pip
     python3=/opt/conda/bin/python
     export conda pip python3

%runscript
     echo "Starting notebook..."
     echo "Open browser to localhost:8888"
     exec /opt/conda/bin/jupyter notebook --notebook-dir=/projects --allow-root --port=8888 --no-browser

%post   
     # Update conda packages
     /opt/conda/bin/conda update --all -y --quiet
     # Install conda packages
     /opt/conda/bin/conda install -c conda-forge -y -q pip matplotlib tqdm jupyter cython scipy numpy pandas scikit-learn seaborn lightgbm tensorflow 
     /opt/conda/bin/conda install -c conda-forge -y -q tornado=5.1.1
     # Update pip
     /opt/conda/bin/pip install -U pip -q
     # Install additional packages
     /opt/conda/bin/pip install keras pydot
     # Clean up
     /opt/conda/bin/conda clean --all -y --quiet
     apt-get autoremove -y
     apt-get clean
     # create bind points for HPCC environment
     mkdir -p /projects

%test  
     echo "Testing python..."
     /opt/conda/bin/python -V
