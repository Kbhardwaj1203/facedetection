# Use a stable Python image
FROM python:3.10-slim

# Install system dependencies required for dlib and face-recognition
RUN apt-get update && apt-get install -y \
    build-essential \
    cmake \
    libopenblas-dev \
    liblapack-dev \
    libx11-dev \
    libgtk-3-dev \
    libboost-all-dev \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Set working directory
WORKDIR /app

# Copy files
COPY . .

# Install Python dependencies
RUN pip install --upgrade pip
RUN pip install -r requirements.txt

# Expose port
EXPOSE 5000

# Set environment variables
ENV PORT=5000

# Start the app using Gunicorn and your wsgi.py file
CMD ["gunicorn", "-b", "0.0.0.0:5000", "wsgi:app"]
