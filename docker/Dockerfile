# syntax=docker/dockerfile:1.4
FROM python:3.11-slim

# Set the working directory
WORKDIR /app

# Copy and install dependencies
COPY --link requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the marimo application file
COPY --link app.py .

# Expose the default marimo application port
EXPOSE 8080

# Create and switch to a non-root user for security
RUN useradd -m app_user
USER app_user

# Run marimo targeting all network interfaces
CMD [ "marimo", "run", "app.py", "--host", "0.0.0.0", "-p", "8080" ]

