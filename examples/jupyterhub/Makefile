.PHONY: jupyterhub

@ JUPYTERHUB_DATA=$(PWD)/input/jupyterhub/notebooks

jupyterhub:
	@ docker run -p 8000:8000 -d --name jupyterhub jupyterhub/jupyterhub jupyterhub

jupyterhub:
	@ mkdir -p $(PWD)/input/jupyterhub
	@ mkdir -p $(PWD)/input/jupyterhub/notebooks
	# jupyterhub --ip 10.0.1.2 --port 443 --ssl-key my_ssl.key --ssl-cert my_ssl.cert
	docker run -v $(JUPYTERHUB_DATA):/home -p 8000:8000 --rm -d --name jupyterhub agilelabtest/jupyterhub jupyterhub -f /etc/jupyter/jupyter_notebook_config.py
