FROM node:18-slim 
RUN apt-get update || : && apt-get install -y \
    python3 \
    python3-pip \
    build-essential \
    python3-venv \
    python3-dev \
    gcc \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Install Python dependencies
RUN pip3 install --break-system-packages -U \
    pandas \
    numpy \
    scikit-learn \
    matplotlib \
    python-dotenv \
    requests \
    seaborn

WORKDIR /usr/app

COPY package*.json ./
# Manually copy the two Python files to matching paths in the image
# Reference file paths using environment variables (set in .env)
ARG AI_ADDRESS_1
ARG AI_ADDRESS_2

COPY . .

# copy files in the ai directory to the a folder name ai in the home directory of the image

  
WORKDIR /usr/app

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "npm", "start" ]