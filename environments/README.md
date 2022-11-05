# Environments

PwnをするときのDocker環境。

## Build
約3分かかる。
```
docker build -t pwn-ubuntu22.04 environments/ubuntu22.04/
```

## Run

このリポジトリのchallengesディレクトリをマウントする。

```
docker run -v $(pwd)/challenges:/home/pwn/challenges -it pwn-ubuntu22.04 
```

