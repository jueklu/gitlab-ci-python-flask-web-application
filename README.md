# gitlab-ci-python-flask-web-application
GitLab CI Pipeline the containerizes and deploys a Python Flask web application. 

<br>

Different Dockerfiles are provided to deploy either the Python code, the compiled Python Bytecode, ore the compiled Python Binary.

Define the Dockerfile to use via the DOCKERFILE variable in the CI pipeline manifest, for example: "Dockerfile_PythonCode", "Dockerfile_Multistage_Bytecode", "Dockerfile_Multistage_Binary"