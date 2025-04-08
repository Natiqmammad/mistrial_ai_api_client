
```markdown
# Mistral AI API Client for Rust

[![Crates.io](https://img.shields.io/crates/v/mistral-client.svg)](https://crates.io/crates/mistral_api_client)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](https://github.com/natiqmammad/mistrial_ai_api_client)
[![Docs.rs](https://docs.rs/mistral_api_client/badge.svg)](https://docs.rs/mistral_api_client)

Unofficial Rust client for Mistral AI's API. Async-ready, strongly typed, and designed for reliability.

## Features

- 🚀 Full async support using Tokio
- 🔒 Strong type safety
- ⚙️ Configurable client parameters
- 🛠️ Comprehensive error handling
- 📦 Zero unsafe code

## Installation

Add to your `Cargo.toml`:
```toml
[dependencies]
mistral_api_client = "0.1"
tokio = { version = "1.0", features = ["full"] }
```

## Quick Start

```rust
use mistral_api_client::MistralClient;

#[tokio::main]
async fn main() {
    let client = MistralClient::new("your-api-key-here")
        .with_model("mistral-large-latest")
        .with_temperature(0.7);

    match client.generate("Explain quantum computing in simple terms").await {
        Ok(response) => println!("AI Response:\n{}", response),
        Err(e) => eprintln!("Error: {}", e),
    }
}
```

## Usage

### Client Configuration

```rust
let client = MistralClient::new("API_KEY")
    .with_api_url("https://custom.endpoint") // Optional
    .with_model("mistral-medium")            // Default: mistral-large-latest
    .with_temperature(0.5)                   // Default: 0.7
    .with_max_tokens(1000);                  // Default: 2000
```

### Error Handling

```rust
match client.generate("...").await {
    Ok(response) => /* handle success */,
    Err(MistralError::ApiError(e)) => /* handle API errors */,
    Err(MistralError::NetworkError(e)) => /* handle network issues */,
    Err(MistralError::MissingApiKey) => /* handle missing key */,
}
```

## Examples

### Basic Chat Completion

```rust
use mistral_api_client::{MistralClient, ChatMessage};

#[tokio::main]
async fn main() {
    let client = MistralClient::new("your-api-key");
    
    let messages = vec![
        ChatMessage {
            role: "user".to_string(),
            content: "Write a Rust function to calculate Fibonacci numbers".to_string(),
        }
    ];

    let response = client.generate(&messages[0].content).await.unwrap();
    println!("{}", response);
}
```

## API Requirements

1. Mistral AI API key - [Get from Mistral](https://console.mistral.ai/)
2. Rust 1.60+

## Contributing

Contributions welcome! Please:
1. Open an issue for discussion
2. Fork the repository
3. Create a feature branch
4. Submit a PR

## License

Dual-licensed under either:
- MIT License ([LICENSE-MIT](LICENSE-MIT))
- Apache License 2.0 ([LICENSE-APACHE](LICENSE-APACHE))

```


**FEATURES:**
- Interactive code examples
- Badges for versioning and docs
- Clear installation instructions
- Error handling examples
- Contribution guidelines
- Mobile-friendly formatting
