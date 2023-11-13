# Environments

PwnをするときのDocker環境。

## Build

リポジトリのルートディレクトリで実行する。
約3分かかる。

```
docker build -t pwn-ubuntu22.04 environments/ubuntu22.04/
```

## Create

```
docker create --name pwn-ubuntu22.04 -v $(pwd):/home/pwn/ctf -it pwn-ubuntu22.04
```

```
docker create --name pwn-ubuntu22.04 -v $(pwd):/home/pwn/ctf -it pwn-ubuntu22.04 -p 8888:8888
```

## Start

```
docker start -ai pwn-ubuntu22.04
```

## Run

`docker run`でも良いが、`docker create`と`docker start`の方が便利。

```
docker run -v $(pwd)/challenges:/home/pwn/challenges -it pwn-ubuntu22.04 
```

```
docker run -v $(pwd)/challenges:/home/pwn/challenges --cap-add=SYS_PTRACE --security-opt seccomp=unconfined -it pwn-ubuntu22.04 
```
