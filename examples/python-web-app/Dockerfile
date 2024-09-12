# Use the official Python slim image
FROM python:3.9-slim

# Set the working directory in the container
WORKDIR /app

# Copy the requirements.txt to the working directory
COPY requirements.txt /app/

# Install system dependencies and Python dependencies
RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    tzdata \
    && pip install --no-cache-dir -r requirements.txt \
    && rm -rf /var/lib/apt/lists/*

# Copy the rest of the application code
COPY devops /app/devops

# Expose the port that Django uses
EXPOSE 8000

# Command to run the Django development server
CMD ["python3", "devops/manage.py", "runserver", "0.0.0.0:8000"]
