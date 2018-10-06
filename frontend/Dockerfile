FROM python:2.7.15-stretch
WORKDIR /app
RUN apt-get update
RUN apt-get install -y git locales locales-all
RUN git clone https://github.com/webtobesocial/leaks.git /app
RUN pip install -r requirements.txt
COPY . /app
ENTRYPOINT ["python"]
CMD ["app.py"]
