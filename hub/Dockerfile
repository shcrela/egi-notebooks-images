# Starting with the image used in helm jupyterhub-v0.7-10de8dc
FROM jupyterhub/k8s-hub:b4779dc

# install d4science auth plugin for using the service in D4Science
USER root
RUN pip3 install git+https://github.com/enolfc/d4scienceauth.git@v0.3

# install oauthenticator with EGI Check-in, with refresh
RUN pip3 install git+https://github.com/enolfc/oauthenticator@checkin

# install the EGI Spawner
RUN pip3 install git+https://github.com/enolfc/egispawner

# Customise Jupyter login
# TODO(enolfc): this can break quite easily, should find a better way
COPY login.html /usr/local/share/jupyterhub/templates/login.html
COPY 401.html /usr/local/share/jupyterhub/templates/401.html

COPY egi-notebooks.png /usr/local/share/jupyterhub/static/images/jupyter.png

ARG NB_USER=jovyan
USER ${NB_USER}
