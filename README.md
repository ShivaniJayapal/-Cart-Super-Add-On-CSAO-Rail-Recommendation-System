# Cart-Super-Add-On-CSAO-Rail-Recommendation-System
**Methodology & Model Architecture**

The recommendation engine follows a two-stage “Retrieve and Rank” pipeline designed to balance speed and predictive accuracy.

**Phase A: Retrieval Layer (Statistical)**
Algorithm: Apriori (Association Rule Mining)
Function: Identifies globally frequent item pairings using metrics such as Support and Lift
Storage: Generated rules are cached in Redis as a key-value store to enable constant-time (O(1)) lookup

**Phase B: Ranking Layer (Neural)**
Algorithm: Behavioral Sequence Transformer (BST)
Function: Processes the sequence of items in a user’s cart using self-attention mechanisms to predict the most relevant next add-on


**Technical Implementation & Scalability**

The system is implemented as a Python-based microservice with the following technology stack:

FastAPI: High-performance asynchronous API framework for serving recommendations
Redis: Used as a feature store for caching association rules
PyTorch: Framework for building and serving the Transformer-based ranking model
Uvicorn: Production-grade ASGI server
Scalability Strategy
Containerization: The service is designed for deployment using Docker
Load Balancing: In production, orchestration tools like Kubernetes can be used to auto-scale FastAPI instances during peak traffic hours (e.g., 7 PM – 10 PM)

**Final Results & Evaluation**
Performance Metrics
Inference Latency: 54.81 ms (measured in a local environment)
