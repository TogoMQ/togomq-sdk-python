# Quick Start Guide

Get started with TogoMQ SDK for Python in 5 minutes!

## 1. Installation

```bash
pip install togomq-sdk
```

## 2. Get Your Token

Visit [https://togomq.io](https://togomq.io) and get your authentication token.

## 3. First Publish

Create a file `publish_example.py`:

```python
from togomq import Client, Config, Message

# Configure client
config = Config(token="your-token-here")

# Create and connect
with Client(config) as client:
    # Create a message
    message = Message("my-topic", b"Hello TogoMQ!")
    
    # Publish it
    response = client.pub_batch([message])
    print(f"✅ Published {response.messages_received} message(s)")
```

Run it:
```bash
python publish_example.py
```

## 4. First Subscribe

Create a file `subscribe_example.py`:

```python
from togomq import Client, Config, SubscribeOptions

# Configure client
config = Config(token="your-token-here")

# Create and connect
with Client(config) as client:
    # Subscribe to topic
    options = SubscribeOptions("my-topic")
    msg_gen, err_gen = client.sub(options)
    
    # Receive messages
    print("📨 Waiting for messages...")
    for msg in msg_gen:
        print(f"Received: {msg.body.decode()}")
        print(f"From topic: {msg.topic}")
        print(f"UUID: {msg.uuid}")
```

Run it (in a separate terminal):
```bash
python subscribe_example.py
```

## 5. Advanced Usage

### With Metadata

```python
message = Message("orders", b'{"order_id": 123}')
message.with_variables({
    "priority": "high",
    "customer_id": "CUST-123"
})
client.pub_batch([message])
```

### With Delay and Retention

```python
message = Message("scheduled-task", b"Task data")
message.with_postpone(60)       # Delay 60 seconds
message.with_retention(3600)    # Keep for 1 hour
client.pub_batch([message])
```

### Wildcard Subscriptions

```python
# Subscribe to all topics
options = SubscribeOptions("*")

# Subscribe to pattern
options = SubscribeOptions("orders.*")  # orders.new, orders.updated, etc.
```

### With Rate Limiting

```python
options = SubscribeOptions("events")
options.with_batch(10)           # Max 10 messages at once
options.with_speed_per_sec(100)  # Max 100 messages per second
```

### Error Handling

```python
from togomq import TogoMQError, ErrorCode

try:
    client.pub_batch(messages)
except TogoMQError as e:
    if e.code == ErrorCode.AUTH:
        print("Authentication failed!")
    elif e.code == ErrorCode.CONNECTION:
        print("Connection error!")
    else:
        print(f"Error: {e}")
```

## 6. Best Practices

✅ **DO:**
- Use context manager (`with` statement)
- Reuse client instances
- Handle errors appropriately
- Set appropriate log levels
- Close connections when done

❌ **DON'T:**
- Forget to close client
- Ignore errors
- Create new client for each request
- Publish messages without topics
- Commit tokens to git

## 7. Configuration Options

```python
config = Config(
    token="your-token",           # Required
    host="q.togomq.io",          # Optional (default)
    port=5123,                    # Optional (default)
    log_level="info",            # Optional: debug, info, warn, error, none
    use_tls=True,                # Optional (default: True)
)
```

## 8. Logging

```python
# Development - verbose logging
config = Config(token="...", log_level="debug")

# Production - errors only
config = Config(token="...", log_level="error")

# Silent
config = Config(token="...", log_level="none")
```

## 9. Complete Example

```python
from togomq import Client, Config, Message, SubscribeOptions
import threading

def publisher():
    """Publish messages."""
    config = Config(token="your-token")
    with Client(config) as client:
        for i in range(10):
            msg = Message("demo", f"Message {i}".encode())
            client.pub_batch([msg])
            print(f"📤 Published message {i}")

def subscriber():
    """Receive messages."""
    config = Config(token="your-token")
    with Client(config) as client:
        options = SubscribeOptions("demo")
        msg_gen, _ = client.sub(options)
        
        for msg in msg_gen:
            print(f"📥 Received: {msg.body.decode()}")

# Run both
sub_thread = threading.Thread(target=subscriber)
pub_thread = threading.Thread(target=publisher)

sub_thread.start()
pub_thread.start()

pub_thread.join()
sub_thread.join()
```

## 10. Next Steps

- 📚 Read the [full documentation](README.md)
- 💡 Check out [examples](examples/)
- 🐛 Report issues on [GitHub](https://github.com/TogoMQ/togomq-sdk-python/issues)
- 🌐 Visit [TogoMQ website](https://togomq.io)

## Environment Variables

Store your token securely:

```bash
export TOGOMQ_TOKEN="your-token-here"
```

Then in code:
```python
import os
config = Config(token=os.getenv("TOGOMQ_TOKEN"))
```

## Troubleshooting

**Connection Error?**
- Check your token is valid
- Verify network connectivity
- Ensure firewall allows port 5123

**Authentication Failed?**
- Verify token is correct
- Check token hasn't expired

**Import Error?**
- Ensure package is installed: `pip list | grep togomq`
- Reinstall: `pip install --upgrade togomq-sdk`

## Getting Help

- 📖 Documentation: https://togomq.io/docs
- 💬 GitHub Issues: https://github.com/TogoMQ/togomq-sdk-python/issues
- 📧 Email: info@togomq.io

---

**Happy messaging with TogoMQ! 🚀**
