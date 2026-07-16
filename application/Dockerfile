FROM python:3.14.4

WORKDIR /app

COPY application/source-code/requirements.txt .

RUN pip install -r requirements.txt

COPY application/source-code/ .

EXPOSE 5000

CMD ["python", "app.py"]
