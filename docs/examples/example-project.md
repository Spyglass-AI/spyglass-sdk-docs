# Example Project

A complete working example of Spyglass integration.

## Overview

The [Spyglass Example Project](../../../example-project/) demonstrates a complete integration of the Spyglass SDK with a real application. This example shows:

- Basic SDK setup and configuration
- OpenAI API tracing
- Function tracing with decorators
- Deployment tracking with GitHub Actions
- Model and prompt management

## Project Structure

```
example-project/
├── spyglass-example-project/
│   ├── main.py              # Main application with tracing
│   ├── model.yaml           # Model and prompt configuration
│   ├── pyproject.toml       # Python dependencies
│   └── .env.example         # Environment variables template
├── .github/workflows/
│   └── spyglass.yaml        # Deployment tracking workflow
└── README.md                # Project documentation
```

## Key Features Demonstrated

### 1. Basic Tracing

```python
from spyglass_ai import spyglass_openai, spyglass_trace
import openai

# Wrap OpenAI client
client = spyglass_openai(openai.OpenAI())

# Trace function calls
@spyglass_trace()
def call_openai_chat_api(model, system_prompt):
    completion = client.chat.completions.create(
        model=model,
        messages=[
            {"role": "system", "content": system_prompt},
            {"role": "user", "content": "Tell me a joke with only two sentences."}
        ]
    )
    return completion.choices[0].message.content
```

### 2. Configuration Management

The `model.yaml` file manages model and prompt configuration:

```yaml
name: "Spyglass Example Project"
description: "Example project for Spyglass AI Platform"
model: "gpt-4.1-nano"
prompt: |
  You are a helpful AI assistant that provides accurate and concise information.
  Always be polite and professional in your responses.
  If you're unsure about something, acknowledge your uncertainty.
```

### 3. Deployment Tracking

The GitHub Actions workflow automatically tracks deployments:

```yaml
- name: Update Spyglass Deployments
  uses: spyglass-ai/spyglass-deployments-action@v1.2
  env:
    SPYGLASS_API_KEY: ${{ secrets.SPYGLASS_API_KEY }}
    DEPLOYMENT_ID: 'spyglass-example-project'
    MODEL_FILE_PATH: 'spyglass-example-project/model.yaml'
```

## Running the Example

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd example-project/spyglass-example-project
   ```

2. **Install dependencies**:
   ```bash
   pip install -e .
   ```

3. **Configure environment**:
   ```bash
   cp .env.example .env
   # Edit .env with your API keys
   ```

4. **Run the application**:
   ```bash
   python main.py
   ```

## What You'll See

- **Console Output**: Real-time logging of API calls
- **Spyglass Dashboard**: Live traces and metrics
- **Deployment Tracking**: Model and prompt changes over time

## Key Learnings

1. **Minimal Code Changes**: The example shows how little code is needed to add comprehensive tracing
2. **Production Ready**: Includes deployment tracking and configuration management
3. **Real-time Monitoring**: See your AI application's performance in real-time
4. **Error Detection**: Automatically catch and debug issues

## Next Steps

- [Installation Guide](../getting-started/installation.md) - Set up Spyglass in your own project
- [OpenAI Tracing Guide](../guides/openai-tracing.md) - Advanced tracing techniques
- [Deployment Tracking Guide](../guides/deployment-tracking.md) - Production monitoring
- [API Reference](../api-reference/) - Complete API documentation

## Source Code

View the complete example project at: [example-project/](../../../example-project/) 