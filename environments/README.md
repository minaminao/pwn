# Environments

PwnをするときのDocker環境。

## Build

リポジトリのルートディレクトリで実行する。
約3分かかる。

```
docker build -t pwn-ubuntu22.04 environments/ubuntu22.04/
```

## Run

このリポジトリのchallengesディレクトリをマウントする。

```
docker run -v $(pwd)/challenges:/home/pwn/challenges -it pwn-ubuntu22.04 
```

```
docker run -v $(pwd)/challenges:/home/pwn/challenges --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -it pwn-ubuntu22.04 
```
