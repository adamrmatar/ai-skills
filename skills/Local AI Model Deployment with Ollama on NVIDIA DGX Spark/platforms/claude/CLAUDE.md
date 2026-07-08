# Claude Code Custom Instructions - Local Ai Model Deployment With Ollama On Nvidia Dgx Spark
> Skill for deploying and running local AI models using Ollama on NVIDIA DGX Spark hardware, including model download, inference execution, and integration with coding tools like Claude.

# Local AI Model Deployment with Ollama on NVIDIA DGX Spark

## Overview
This skill enables you to deploy and run AI models locally on NVIDIA DGX Spark hardware using Ollama. Key capabilities include:
- Local model management (download/version control)
- GPU-accelerated inference
- Integration with development tools like Claude

See hardware requirements in [Hardware Setup](references/hardware_setup.md).

## Step-by-Step Workflow

1. **System Setup**
   - Connect power and peripherals as detailed in [Hardware Setup](references/hardware_setup.md)
   - Boot system and complete Ubuntu initialization

2. **Ollama Installation**
   ```bash
   curl -fsSL https://ollama.ai/install.sh | sh
   ```

3. **Model Download**
   ```bash
   ollama pull gemma:4b  # 9.6GB version
   ollama pull gemma:31b # 20GB version (optional)
   ```

4. **Basic Inference Test**
   ```bash
   ollama run gemma:4b
   ```
   - Verify response quality and speed
   - Monitor GPU utilization in DGX Dashboard

5. **Advanced Integration (with Claude)**
   ```bash
   # Install Claude
   sudo apt install claude-code
   
   # Launch with specific model
   mkdir project
   cd project
   ollama launch claude --model gemma:31b
   ```

## Code Generation Example
```python
# Prompt template for web development
prompt = """Create a static HTML website for yoga accessories with:
1. Responsive navbar
2. Three product cards with images
3. Minimal CSS (inline styles)
4. Contact form placeholder"""

# Send to local model
response = ollama.generate(
    model="gemma:4b",
    prompt=prompt,
    temperature=0.5
)
```

## Best Practices
1. **Model Selection**:
   - Use 4B model for quick prototyping
   - Switch to 31B for production-quality output

2. **Resource Management**:
   - Close unused applications during large model runs
   - Monitor memory usage via DGX Dashboard

3. **Prompt Engineering**:
   - Be specific about output format requirements
   - Include length constraints (e.g., "answer in 3 lines")

## Common Pitfalls
1. **Insufficient Storage**:
   - 31B model requires 20GB+ free space
   - Solution: Clean up unused models with `ollama rm <model>`

2. **GPU Memory Errors**:
   - Symptom: "CUDA out of memory" errors
   - Solution: Use smaller batch sizes or model variants

3. **Stale Model Versions**:
   - Always specify version tag (e.g., `gemma:4b` not just `gemma`)
   - Update models periodically with `ollama pull`

## Validation Steps
1. **Basic Sanity Check**:
   ```bash
   ollama run gemma:4b "Explain quantum computing in simple terms"
   ```
   - Verify coherent response within 5 seconds

2. **GPU Utilization Test**:
   - Run complex query while monitoring DGX Dashboard
   - Expect 50-80% GPU utilization spikes

3. **Code Generation Test**:
   - Generate Python file handling code
   - Verify executable output with `python3 generated_code.py`

For advanced use cases, see [Local Inference Applications](references/local_inference_applications.md).

# Detailed Guidelines

## Hardware Setup

# NVIDIA DGX Spark Hardware Setup Guide

## Physical Connections
1. **Power Connection**: Connect the power cord to the first USB port adjacent to the power button
2. **Peripheral Setup**:
   - Use USB-C docking station for multi-monitor support (HDMI connections)
   - Connect keyboard/mouse via Bluetooth or wired USB
3. **Boot Process**:
   - Press the small power button (boot is silent with no audible indicators)
   - System runs Ubuntu-based OS with custom NVIDIA interface

## Hardware Specifications
- **Architecture**: NVIDIA Grace Blackwell (unified CPU/GPU chip)
- **Cores**: 20 ARM cores (10 Cortex + 10 additional Cortex)
- **Performance**: 1 petaflop (10^15) 4-bit floating point operations
- **Memory Bandwidth**: 273 GB/s
- **Storage**: 4TB SSD
- **GPU Specs**:
  - 6,144 CUDA cores
  - Supports models up to 200B parameters

## Monitoring
Access the DGX Dashboard to view:
- Real-time memory usage (128GB total)
- GPU utilization percentages
- System temperature and performance metrics

## Best Practices
1. Always verify peripheral connections before power-on
2. Monitor initial boot via connected displays (no audio cues)
3. Keep system firmware updated through Ubuntu package manager
4. Use the specification page as reference for model compatibility checks

## Local Inference Applications

# Practical Applications of Local Inference

## Code Generation Workflow
1. **Project Setup**:
   ```bash
   mkdir project_folder
   cd project_folder
   ```

2. **Launch Development Environment**:
   ```bash
   ollama launch claude
   ```

3. **Prompt Engineering Example**:
   ```
   Create a static HTML website for yoga accessories with:
   - Homepage with hero image section
   - Product catalog grid (3 items)
   - About and Contact pages
   - Minimal CSS styling
   ```

## Performance Optimization
- **Batch Processing**: Chain multiple related queries in single session
- **Parameter Tuning**:
  ```bash
  ollama run gemma:4b --temperature 0.7 --top_k 40
  ```

## Resource Monitoring
- Watch GPU utilization during:
  - Model loading phase (initial spike)
  - Generation phase (sustained usage)
  - Idle state (should return to baseline)

## Common Use Cases
1. **Local Chat Interface**:
   ```bash
   ollama run gemma:4b
   ```
   - Works offline after initial download
   - No API rate limits

2. **Document Processing**:
   ```
   Summarize this technical document in 3 bullet points:
   [paste document text]
   ```

3. **Prototyping**:
   ```
   Generate Python Flask API skeleton for:
   - User authentication
   - Product inventory management
   - JSON responses
   ```

## Limitations
- No built-in persistence (chat history not saved)
- Smaller models may produce less accurate results
- Hardware constraints for very large models

## Ollama Workflows

# Ollama Model Management Guide

## Installation
```bash
curl -fsSL https://ollama.ai/install.sh | sh
```

## Model Operations
1. **Listing Available Models**:
   ```bash
   ollama list
   ```

2. **Downloading Models**:
   ```bash
   ollama pull gemma:4b  # 4B parameter version
   ollama pull gemma:31b # 31B parameter version (20GB)
   ```

3. **Running Inference**:
   ```bash
   ollama run gemma:4b
   ```
   - First run triggers automatic download if missing
   - Subsequent runs use local cached version

## Model Selection Criteria
- **Gemma 4B**: 9.6GB download, faster inference for smaller tasks
- **Gemma 31B**: 20GB download, higher accuracy for complex tasks

## Performance Characteristics
- Initial query latency: 2-5 seconds (model loading)
- Subsequent queries: sub-second responses
- GPU utilization spikes during generation (monitor via DGX Dashboard)

## Common Issues
1. **Download Interruptions**: Resume partial downloads with same pull command
2. **Memory Errors**:
   - For 31B model: Ensure 20GB+ free memory
   - Close other memory-intensive applications
3. **Version Conflicts**: Explicitly specify model tags (e.g., gemma:4b vs gemma:latest)

## Integration Example with Claude
```bash
ollama launch claude --model gemma:31b
```
- Requires prior Claude installation
- Model specification overrides default

## Sources

# Video Sources

The following curated videos were synthesized to create this skill:

1. **[NVIDIA DGX Spark - AI Supercomputer: First Impressions](https://www.youtube.com/watch?v=FW8bCjhl3zE)** by codebasics