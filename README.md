**[Technical Overview](#technical-overview)** |
With [JupyterHub](https://jupyterhub.readthedocs.io) you can create a
**multi-user Hub** which spawns, manages, and proxies multiple instances of the
single-user [Jupyter notebook](https://jupyter-notebook.readthedocs.io)
server.

[Project Jupyter](https://jupyter.org) created JupyterHub to support many
users. The Hub can offer notebook servers to a class of students, a corporate
data science workgroup, a scientific research project, or a high performance
computing group.

## Technical overview

Three main actors make up JupyterHub:

- multi-user **Hub** (tornado process)
- configurable http **proxy** (node-http-proxy)
- multiple **single-user Jupyter notebook servers** (Python/Jupyter/tornado)

Basic principles for operation are:

- Hub launches a proxy.
- Proxy forwards all requests to Hub by default.
- Hub handles login, and spawns single-user servers on demand.
- Hub configures proxy to forward url prefixes to the single-user notebook
  servers.

JupyterHub also provides a
[REST API](http://petstore.swagger.io/?url=https://raw.githubusercontent.com/jupyter/jupyterhub/master/docs/rest-api.yml#/default)
for administration of the Hub and its users.
