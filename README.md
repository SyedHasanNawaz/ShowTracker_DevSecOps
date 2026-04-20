🛡️ Secure ShowTracker: DevSecOps Pipeline 

A production-grade TV show tracking backend built with FastAPI and MongoDB, designed to demonstrate secure containerization and automated CI/CD security scanning. 
🔑 The DevSecOps Focus 

This project is not just about writing API endpoints. It is about building a secure software supply chain. The pipeline ensures that vulnerable code never makes it to production. 

     SAST (Static Analysis): Bandit scans raw Python code for security flaws (e.g., hardcoded passwords) before the application is even packaged.
     Container Security: The app is packaged into a lightweight Docker container.
     Image Scanning: Trivy scans the final Docker image for known CVEs (both OS-level and Python dependencies).
     Shift-Left Security: If a HIGH or CRITICAL vulnerability is detected, the GitHub Actions pipeline fails immediately, blocking the deployment.
     

🏗️ Architecture 

     Backend: Python 3.12 / FastAPI
     Database: MongoDB (Orchestrated via Docker Compose)
     Containerization: Docker (Multi-environment support)
     CI/CD: GitHub Actions
     Security Tools: Bandit, Trivy
     Registry: Docker Hub
     

🚀 The Pipeline 

Every push to the main branch triggers the following automated workflow: 

    Code Checkout 
    Bandit Scan (Fails on Medium/High Python flaws) 
    Docker Build (Packages the application) 
    Trivy Scan (Fails on HIGH/CRITICAL CVEs) 
    Docker Push (Uploads secured image to Docker Hub) 

🐳 Quick Start (Using Docker Compose) 

    Clone the repository: 
    bash
     
      
     
    git clone https://github.com/SyedHasanNawaz/ShowTracker_DevSecOps.git
     
     
      

    Create a .env file in the root directory (variables are safely excluded from Git): 
    env
     
      
     
    MONGO_USER=admin
    MONGO_PASS=your_secure_password
    SECRET_KEY=your_jwt_secret
    MONGO_URI=mongodb://admin:your_secure_password@mongo:27017/Show_Tracker?authSource=admin
     
     
      

    Spin up the backend and database: 
    bash
     
      
     
    docker compose --env-file .env up -d --build
     
     
      

    Access the interactive API documentation:
    http://localhost:8000/docs   

📂 Core API Endpoints 

     POST /users/register - Create a new user
     POST /users/login - Authenticate and receive JWT
     GET /shows/ - Fetch TV show catalog
     POST /watchlist/ - Add shows to user watchlist
     

(Full endpoint list available at the /docs Swagger UI) 
✍️ Author 

Syed Hasan Nawaz | (https://www.linkedin.com/in/syed-hasan-nawaz-384b26362/) | Docker Hub  
