FROM pytorch/pytorch:1.12.1-cuda11.3-cudnn8-devel
# Set the working directory
WORKDIR /workspace

# Install Jupyter Notebook
RUN pip install notebook jupyterlab numpy pandas matplotlib seaborn scikit-learn kaggle jedi ipython ipywidgets tqdm

# RUN jupyter lab build

RUN jupyter nbextension enable --py widgetsnbextension --sys-prefix

# Set up an environment variable for the Jupyter password
ENV JUPYTER_PASSWORD=""

# Expose the Jupyter Notebook port
EXPOSE 8888

RUN whoami

RUN mkdir -p /root/.jupyter
RUN mkdir -p /root/.ipython/profile_default

ENTRYPOINT ["sh", "-c", "hashed_password=$(python -c 'from notebook.auth import passwd; print(passwd(\"$JUPYTER_PASSWORD\"))'); echo \"c.NotebookApp.password = '$hashed_password'\" >> /root/.jupyter/jupyter_notebook_config.py && echo \"c.InteractiveShellApp.extensions.append('autoreload')\" >> /root/.ipython/profile_default/ipython_config.py && echo \"c.InteractiveShellApp.exec_lines.append('%load_ext autoreload')\" >> /root/.ipython/profile_default/ipython_config.py && echo \"c.InteractiveShellApp.exec_lines.append('%autoreload 2')\" >> /root/.ipython/profile_default/ipython_config.py && echo \"c.IPCompleter.greedy=True\" >> /root/.ipython/profile_default/ipython_config.py && jupyter nbextension enable --py widgetsnbextension --sys-prefix && jupyter lab --ip=0.0.0.0 --port=8888 --allow-root --no-browser --NotebookApp.token='' --NotebookApp.password=''"]
