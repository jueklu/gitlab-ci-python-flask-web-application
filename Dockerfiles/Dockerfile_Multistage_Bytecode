### Stage 1: Compile Python Application

# Use Python-slim image as the base image / Label image as "builder"
FROM python:3.13-slim AS builder

# Set the working directory inside the container to /app
WORKDIR /app

# Copy the contents of the "flask-app" directory to "/app" inside the container
ADD flask-app/. /app

# Install the dependencies listed in "requirements.txt"
RUN pip install -r requirements.txt

# Compile all Python files to bytecode and move the desired one to /app as app.pyc
RUN python -m compileall .



### Stage 2: Final Container with Bytecode

# Use a lightweight Python image for the final stage
FROM python:3.13-rc-alpine

# Copy requirements.txt from builder
COPY --from=builder /app/requirements.txt /tmp/   

# Install app requirements
RUN pip install -r /tmp/requirements.txt

# Create system user "appuser" / no PW
RUN adduser -S -D -H -h /app appuser

# Switch to "appuser"
USER appuser

# Copy compiled .pyc files and any necessary files from the builder stage
COPY --from=builder /app/__pycache__/* /app/

# Define working directory
WORKDIR /app

# Expose port 8080 for the application
EXPOSE 8080

# Execute Bytecode when the container starts
ENTRYPOINT ["python", "/app/app.cpython-313.pyc"]
