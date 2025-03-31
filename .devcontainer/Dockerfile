FROM mcr.microsoft.com/vscode/devcontainers/python:3.12

WORKDIR /workspace

RUN curl -fsSL https://deb.nodesource.com/setup_18.x | bash - && \
    apt-get install -y nodejs && \
    npm install -g react-native-cli

RUN apt-get update && \
    apt-get install -y openjdk-11-jdk && \
    mkdir -p /usr/local/android && \
    curl -o /usr/local/android/cmdline-tools.zip https://dl.google.com/android/repository/commandlinetools-linux-8512546_latest.zip && \
    unzip /usr/local/android/cmdline-tools.zip -d /usr/local/android/ && \
    rm /usr/local/android/cmdline-tools.zip

COPY app.py /app/
COPY home.py /app/
COPY login.py /app/
COPY logout.py /app/
COPY register.py /app/
COPY firebase_config.py /app/
COPY requirements.txt /app/

RUN pip install -r /app/requirements.txt

COPY package.json /app/
COPY package-lock.json /app/

RUN npm install --prefix /app

EXPOSE 5000  
EXPOSE 8081  

CMD [ "python", "/app/app.py" ]
