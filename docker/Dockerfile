FROM gurken2108/python3-java

RUN pip3 install esrally

COPY ["rally.ini", "/root/.rally/rally.ini"]

ENTRYPOINT ["esrally"]