FROM maxking/mailman-core:0.4 

SHELL ["/bin/bash", "-l", "-c"]

COPY ./users.py /usr/lib/python3.11/site-packages/mailman/rest
COPY ./addresses.py /usr/lib/python3.11/site-packages/mailman/rest
COPY ./gunicorn.cfg /etc/gunicorn.cfg

