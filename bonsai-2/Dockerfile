FROM debian:bookworm-slim

# Install necessary dependencies
RUN apt-get update && apt-get install -y git build-essential cmake curl python3

# Clone the demo repository
WORKDIR /app
RUN git clone https://github.com/PrismML-Eng/Bonsai-demo.git .

# Setup and download models (this runs during image build)
RUN ./setup.sh

# The standard llama.cpp server needs to bind to 0.0.0.0 to be accessible outside the container
CMD ["./scripts/start_llama_server.sh", "--model", "bonsai-2-27b-ptq1_0", "--port", "8080", "--host", "0.0.0.0"]
