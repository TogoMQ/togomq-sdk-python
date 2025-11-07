# TogoMQ SDK Examples

This directory contains comprehensive examples demonstrating how to use the TogoMQ SDK for Python.

## Examples

- **publish.py** - Publishing examples including:
  - Batch publishing
  - Streaming publishing
  - Custom configuration
  - Error handling
  - Messages with metadata

- **subscribe.py** - Subscription examples including:
  - Basic subscription
  - Advanced subscription with options
  - Wildcard subscriptions
  - Pattern matching
  - Graceful shutdown
  - Error handling
  - Processing with variables

- **complete_workflow.py** - Complete workflow example with:
  - Multiple publishers and subscribers
  - Threading
  - Real-world usage patterns

## Running Examples

1. Install the SDK:
   ```bash
   pip install togomq-sdk
   ```

2. Get your TogoMQ token from https://togomq.io

3. Replace `"your-token-here"` in the examples with your actual token

4. Run an example:
   ```bash
   python publish.py
   python subscribe.py
   python complete_workflow.py
   ```

## Quick Start

```python
from togomq import Client, Config, Message

# Create client
config = Config(token="your-token-here")
client = Client(config)

# Publish a message
messages = [Message("my-topic", b"Hello TogoMQ!")]
response = client.pub_batch(messages)
print(f"Published {response.messages_received} messages")

# Clean up
client.close()
```

## Best Practices

1. **Use context manager** - Always use `with` statement or call `close()`:
   ```python
   with Client(config) as client:
       # Use client
       pass
   ```

2. **Reuse clients** - Create one client per application/thread

3. **Handle errors** - Always wrap in try/except blocks:
   ```python
   from togomq import TogoMQError, ErrorCode
   
   try:
       client.pub_batch(messages)
   except TogoMQError as e:
       if e.code == ErrorCode.AUTH:
           print("Authentication failed")
   ```

4. **Set appropriate log levels** - Use different levels for dev/prod:
   ```python
   config = Config(token="...", log_level="debug")  # Development
   config = Config(token="...", log_level="warn")   # Production
   ```

## Need Help?

- Documentation: https://togomq.io/docs
- GitHub Issues: https://github.com/TogoMQ/togomq-sdk-python/issues
- Website: https://togomq.io
