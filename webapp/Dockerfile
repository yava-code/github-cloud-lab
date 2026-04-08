# Stage 1: install dependencies
FROM python:3.11 AS builder
WORKDIR /install
COPY requirements.txt .
RUN pip install --no-cache-dir --prefix=/install/packages -r requirements.txt

# Stage 2: lean runtime image
FROM python:3.11-slim AS runtime
WORKDIR /app
COPY --from=builder /install/packages /usr/local
COPY app.py .
EXPOSE 5000
CMD ["python", "app.py"]
