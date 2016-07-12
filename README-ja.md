[awslabs/chalice](https://github.com/awslabs/chalice)
---

### 有効なタグと、そのビルドに使われている `Dockerfile`

・latest ([versions/beta/Dockerfile](https://github.com/pottava/dockerized-awslabs-chalice/blob/master/versions/beta/Dockerfile))  
・beta ([versions/beta/Dockerfile](https://github.com/pottava/dockerized-awslabs-chalice/blob/master/versions/beta/Dockerfile))  


# インストール

### Case 1: 環境変数を使う場合

```
cat << EOF >> ~/.bashrc
function chalice () {
  docker run --rm -v \$(pwd):/app \\
      -e AWS_ACCESS_KEY_ID \\
      -e AWS_SECRET_ACCESS_KEY \\
      -e AWS_DEFAULT_REGION \\
      pottava/chalice \$@
}
EOF
source ~/.bashrc
```

### Case 2: クレデンシャルファイルを使う場合

```
cat << EOF >> ~/.bashrc
function chalice () {
  docker run --rm -v \$(pwd):/app \\
      -v $HOME/.aws/credentials:/root/.aws/credentials \\
      pottava/chalice \$@
}
EOF
source ~/.bashrc
```


# 使い方

> 環境変数を使う場合は、そのセット。

```
$ export AWS_ACCESS_KEY_ID=AKIAIOSFODNN7EXAMPLE
$ export AWS_SECRET_ACCESS_KEY=wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY
$ export AWS_DEFAULT_REGION=ap-northeast-1
```

### ・ヘルプの表示

```
$ chalice --help
```

### ・新規プロジェクト作成

```
$ chalice new-project <project-name>
```

### ・プロジェクトのデプロイ

```
$ cd <project-name>
$ chalice deploy
```

### ・ログの表示

```
$ cd <project-name>
$ chalice logs
```
