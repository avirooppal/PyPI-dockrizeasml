# DockerizeAsML

DockerizeAsML is a Python library that allows users to effortlessly dockerize an entire machine learning (ML) project with a single command-line instruction. It automatically recognizes ML model files in the project directory, generates an appropriate Dockerfile, and provides flexibility in configuration.

## Installation

You can install DockerizeAsML using pip:
```
pip install dockerizeasml
```
## Features

- Automatic detection of common ML model file formats (pkl, h5, joblib, pt, pth, onnx, pickle)
- Generation of a Dockerfile tailored to your ML project
- Customizable entry point for your dockerized application
- Flexible port configuration
- Customizable Python version selection
- Support for additional Python package installations
- Easy-to-use command-line interface

## Usage

To dockerize your ML project, navigate to your project's root directory and run:
```
dockerizeasml /path/to/your/ml/project
```
### Advanced Usage

You can customize various aspects of the dockerization process:
```
dockerizeasml /path/to/your/ml/project --entry-point app.py --port 8080 --python-version 3.9 --extra-installs "nltk.downloader -d /usr/local/nltk_data wordnet omw" "pip install some-extra-package"
```

- `--entry-point`: Specify the main Python script (default is app.py)
- `--port`: Set the port to expose (default is 5000)
- `--python-version`: Choose the Python version for the base image (default is 3.9)
- `--extra-installs`: Add additional installation commands (default includes NLTK data download)

## How it works

1. DockerizeAsML scans your project directory for ML model files.
2. It analyzes Python scripts to detect potential model variable names.
3. It generates a Dockerfile that:
   - Uses a Python slim base image
   - Copies and installs the requirements from `requirements.txt`
   - Copies the identified model files
   - Sets environment variables for detected model variables
   - Copies the rest of the project files
   - Configures additional installations (e.g., NLTK data)
   - Exposes the specified port
   - Sets the default command to run your specified entry point

4. You can then use standard Docker commands to build and run your containerized ML project.

## Requirements

- Python 3.6+
- Docker (for building and running the generated Docker image)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

