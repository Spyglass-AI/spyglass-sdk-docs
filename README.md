# Spyglass AI SDK Documentation

This repository contains the documentation for the Spyglass AI SDK - the observability platform for AI applications.

## What is Spyglass?

Spyglass is an observability platform designed specifically for AI applications. It provides:

- **LLM Tracing**: Monitor OpenAI API calls, token usage, and response times
- **Deployment Tracking**: Track model and prompt changes across deployments
- **Performance Analytics**: Identify bottlenecks and optimize your AI applications
- **Error Detection**: Catch and debug issues in production AI systems

## Quick Start

1. **Install the SDK**:
   ```bash
   pip install spyglass-ai
   ```

2. **Set up your API key**:
   ```bash
   export SPYGLASS_API_KEY="your-api-key"
   ```

3. **Start tracing**:
   ```python
   from spyglass_ai import spyglass_openai, spyglass_trace
   import openai
   
   # Wrap your OpenAI client
   client = spyglass_openai(openai.OpenAI())
   
   # Use the @spyglass_trace decorator
   @spyglass_trace()
   def my_ai_function():
       response = client.chat.completions.create(
           model="gpt-4",
           messages=[{"role": "user", "content": "Hello!"}]
       )
       return response
   ```

## Documentation Structure

- **Getting Started**: Installation, configuration, and basic usage
- **SDK Reference**: Complete API reference for the Python SDK
- **Guides**: Step-by-step tutorials and best practices
- **Examples**: Working examples and integration patterns
- **API Reference**: REST API documentation

## Example Project

Check out our [example project](../example-project/) for a complete working example of Spyglass integration.

## Contributing

To contribute to the documentation:

1. Fork this repository
2. Make your changes
3. Submit a pull request

## Support

- **Documentation**: Browse the docs at [docs.spyglass-ai.com](https://docs.spyglass-ai.com)
- **GitHub Issues**: Report bugs or request features
- **Discord**: Join our community for help and discussions 