# Use Ubuntu as the base image
FROM ubuntu

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file and devops directory into the container
COPY requirements.txt /app
COPY devops /app

# Install necessary packages and create a virtual environment
RUN apt-get update && \
    apt-get install -y python3 python3-venv && \
    python3 -m venv /app/venv && \
    /app/venv/bin/pip install --upgrade pip && \
    /app/venv/bin/pip install -r requirements.txt

# Ensure all subsequent commands use the virtual environment
ENV PATH="/app/venv/bin:$PATH"

# Set the default command to run your application
ENTRYPOINT ["python3"]
CMD ["manage.py", "runserver", "0.0.0.0:8000"]
