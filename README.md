# gitlab-ci-python-flask-web-application
GitLab CI Pipeline the containerizes and deploys a Python Flask web application. 

<br>

Different Dockerfiles are provided to deploy either the Python code, the compiled Python Bytecode, ore the compiled Python Binary.

Define the used Dockerfile with the $DOCKERFILE variable in the CI pipeline manifest, for example: "Dockerfile_PythonCode", "Dockerfile_Multistage_Bytecode", "Dockerfile_Multistage_Binary"


### Container Image Name

The build container image name in the GitLab CI pipeline follows this naming convention: `$CI_REGISTRY_IMAGE/$CI_COMMIT_REF_SLUG:$CI_COMMIT_SHA`

- `$CI_REGISTRY_IMAGE` Points to the container registry for the project.

- `$CI_COMMIT_REF_SLUG` Represents the branch or tag.

- `$CI_COMMIT_SHA` Ensures every image is uniquely tied to a specific commit for traceability and reproducibility.