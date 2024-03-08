+++
title = 'Set up'
+++

## Alumni Portal Backend

### How to run

#### Using Python
1. Clone repository locally or on the server
2. Open a shell/command line in this folder (better if it was after activating a python virtual env)
3. Install the needed python packages
```bash
    pip install -r requirements.txt
```
4. Run the python script:
```bash
    python3 main.py
```

#### Using docker
1. Download docker locally or on the server
2. Here the image tag name is `alumni-backend` you can name it as you like
3. Also the port in docker is 8000 by default and you can map it to anything as you like

```bash
docker build -t alumni-backend
docker run -p 8000:8000 -d alumni-backend
```


## Inno-alumni-portal frontend

### How to run or deploy
1. Clone repository locally or on the server
2. Open a shell/command line in this folder
3. To `install` all packages (local to the repo) using `npm`
    ```bash
    npm install
    ```
4. To `build` the project for production
    ```bash
    npm run build
    ```
5. To `start` the project on development
    ```bash
    npm start
    ```
