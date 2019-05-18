JUPYTERHUB_DATA=$(PWD)/input/jupyterhub/notebooks

jupyterhub:
	@ mkdir -p $JUPYTERHUB_DATA
	# jupyterhub --ip 10.0.1.2 --port 443 --ssl-key my_ssl.key --ssl-cert my_ssl.cert
	docker run -v $(JUPYTERHUB_DATA):/home -p 8000:8000 --rm -d --name jupyterhub agilelabtest/jupyterhub jupyterhub -f /etc/jupyter/jupyter_notebook_config.py

.PHONY: jupyterhub
