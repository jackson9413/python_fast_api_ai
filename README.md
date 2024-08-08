# AI Application with FastAPI

This project uses Python FastAPI to build AI applications. It leverages the `transformers` library for model processing and `Pillow` for image handling.


## Setup and Installation

### Prerequisites

- Python 3.9 or higher
- Docker

### Installing Dependencies

To install the required dependencies, run:

```sh
pip install -r requirements.txt
```

## Running the Application
### Locally
To run the application locally, execute:
    ```sh
    uvicorn main:app --reload --port 8000 --host 0.0.0.0
    ```

### Using Docker
To build and run the application using Docker, use the following command:
    ```sh
    docker compose up --build
    ```
Your application will be available at http://localhost:8000.

## API Endpoints
### Root Endpoint
    ```sh
    GET /
    ```
Returns a simple greeting message.

### Ask Endpoint
    ```sh
    POST /ask
    ```
Accepts a text question and an image file, and returns the answer based on the AI model.

### Request Parameters

- [`text`] (str): The question to ask.
- [`image`] (UploadFile): The image file to analyze.

## Model Pipeline

The model pipeline is defined in [`model.py`]. It uses the [`ViltProcessor`] and [`ViltForQuestionAnswering`] from the [`transformers`] library to process the input image and text.

```py
from transformers import ViltProcessor, ViltForQuestionAnswering
from PIL import Image

processor = ViltProcessor.from_pretrained("dandelin/vilt-b32-finetuned-vqa")
model = ViltForQuestionAnswering.from_pretrained("dandelin/vilt-b32-finetuned-vqa")

def model_pipeline(text: str, image: Image):
    # prepare inputs ...
```

## Docker Configuration

The Docker configuration is defined in the [`Dockerfile`] and [`compose.yaml`] The application is built using a multi-stage build to optimize the image size and performance.

## Additional Documentation

For more details on building and running the application with Docker, refer to [`README.Docker.md`].

## References

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Transformers Documentation](https://huggingface.co/transformers/)
- [Pillow Documentation](https://pillow.readthedocs.io/)
- [Docker's Python Guide](https://docs.docker.com/language/python/)
```
