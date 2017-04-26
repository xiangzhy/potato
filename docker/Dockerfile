FROM base_os:0.2

#��װmongodb
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
RUN echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.2 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-3.2.list
RUN apt-get update
RUN apt-get install -y mongodb-org

#��װredis
RUN apt-get install -y redis-server
RUN pip install redis

RUN pip install pymongo

#��װweb���
RUN pip install django==1.8
RUN pip install django-celery

#��װcelery
RUN pip install celery
RUN pip install flower

#����pyter
RUN pip install jupyter

ADD potato /opt/potato
ADD start-all.sh /opt/potato/operator/trademonitor/start-all.sh


ENV PYTHONPATH=/opt/potato
ENV LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/potato/engine/api/ctp:/usr/local/lib

WORKDIR /notebook
# clean up
RUN apt-get autoremove -y; \
    apt-get autoclean -y


EXPOSE 8080
EXPOSE 8888
EXPOSE 5555
EXPOSE 27017