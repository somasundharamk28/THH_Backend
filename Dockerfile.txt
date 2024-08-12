# Use the official Python 3.11 image
FROM python:3.11

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt requirements.txt

# Upgrade pip and setuptools
RUN pip install --upgrade pip setuptools

# Install Python dependencies
RUN pip install -r requirements.txt

# Copy the entire application code into the container
COPY . .

# Copy the model-best directory into the container
COPY model-best /app/model-best

# Expose the port the app runs on
EXPOSE 8082

# Define the command to run the application
CMD [ "python", "app.py" ]
