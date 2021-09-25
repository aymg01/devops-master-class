FROM python:alpine3.10
WORKDIR /app 
COPY requirements.txt /app
RUN pip install --upgrade pip
RUN pip install -r requirements.txt
EXPOSE 5000
COPY . /app
#CMD python ./launch.py

#COPY requirements.txt /app/requirements.txt
ENTRYPOINT ["python", "./launch.py"]
