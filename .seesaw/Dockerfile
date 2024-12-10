FROM python:3.9-slim

WORKDIR /app

# Install git
RUN apt-get update && \
    apt-get install -y git && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY src/ /app/src/
COPY tests/ /app/tests/

# Install the package in development mode
RUN cd /app/src && pip install -e .

EXPOSE 5000

CMD ["python", "-m", "uvicorn", "crator.app:app", "--host", "0.0.0.0", "--port", "5000", "--reload", "--reload-dir", "/app/src"]
