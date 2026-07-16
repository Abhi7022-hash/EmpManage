FROM python:3.14.4

WORKDIR /app

COPY source-code/requirements.txt .

RUN pip install -r requirements.txt

COPY source-code/ .

EXPOSE 5000

CMD ["python", "app.py"]
