FROM ubuntu AS p1

WORKDIR /app 

RUN apt-get update && apt-get install -y python3 python3-pip python3-venv  

# Create and activate a virtual environment
RUN python3 -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install flask  

COPY . . 

FROM python:3.9-alpine  

COPY --from=p1 /app /app  

WORKDIR /app  

EXPOSE 8000

CMD ["/app/venv/bin/python", "app.py"]

