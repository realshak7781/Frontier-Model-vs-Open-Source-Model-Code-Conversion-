
# Code Generation using Different Models

This project demonstrates **code generation** using two powerful language models via Hugging Face Inference Endpoints:

- **CodeQwen1.5-7B-Chat** (`Qwen/CodeQwen1.5-7B-Chat`)
- **CodeGemma-7B-IT** (`google/codegemma-7b-it`)

We send prompts to hosted endpoints and receive generated code snippets in response.

---

## Models Used

| Model | Hugging Face ID | Endpoint URL |
|:---|:---|:---|
| **CodeQwen 1.5-7B-Chat** | `Qwen/CodeQwen1.5-7B-Chat` | [CODE_QWEN_URL](https://h1vdol7jxhje3mpn.us-east-1.aws.endpoints.huggingface.cloud) |
| **CodeGemma 7B IT** | `google/codegemma-7b-it` | [CODE_GEMMA_URL](https://c5hggiyqachmgnqg.us-east-1.aws.endpoints.huggingface.cloud) |

---

## How it Works

1. A prompt is sent to the selected model's **Hugging Face Inference Endpoint**.
2. The model generates a code snippet based on the prompt.
3. The response is processed and displayed.

Both endpoints are deployed on AWS infrastructure through Hugging Face Inference Endpoints.

---

## Example Usage

```python
import requests

def generate_code(prompt, model_url, api_token):
    headers = {
        "Authorization": f"Bearer {api_token}",
        "Content-Type": "application/json"
    }
    payload = {
        "inputs": prompt,
        "parameters": {
            "temperature": 0.2,
            "max_new_tokens": 512
        }
    }
    response = requests.post(model_url, headers=headers, json=payload)
    return response.json()

# Example
prompt = "Write a Python function to check if a number is prime."
model_url = "https://h1vdol7jxhje3mpn.us-east-1.aws.endpoints.huggingface.cloud"  # CodeQwen URL
api_token = "your_huggingface_api_token"

generated = generate_code(prompt, model_url, api_token)
print(generated)
```

---

## Requirements

- Python 3.8+
- `requests` library (`pip install requests`)
- Access to Hugging Face Inference Endpoints (with proper API token)

---

## Notes

- Adjust `temperature`, `max_new_tokens`, and other parameters to fine-tune the generation.
- Make sure your API token has access to the endpoints if they are private.
- You can easily switch between models by changing the `model_url`.

---

## License

This project is licensed under the MIT License.
