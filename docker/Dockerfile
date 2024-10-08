# Use the official Python image from the DockerHub
FROM python:3.10

# Install system dependencies
RUN apt-get update && apt-get install -y \
    libmariadb-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory inside the container
WORKDIR /app

# Copy the requirements file into the container
COPY ./crm/requirements.txt /app/requirements.txt

# Install Python dependencies
RUN pip install --no-cache-dir -r /app/requirements.txt

# Copy the rest of the application code into the container
COPY ./crm /app/crm

# Set environment variables for Django
ENV PYTHONUNBUFFERED=1

# Expose the port the app runs on
EXPOSE 8000

# Set the default command to run the Django server
CMD ["python", "/app/crm/manage.py", "runserver", "0.0.0.0:8000"]
