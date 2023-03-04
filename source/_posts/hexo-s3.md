---
title: Hexo 設定部署到 S3 
date: 2023-02-26 00:25:16
tags: 
  -  HEXO
  -  MINOS
  -  AWS
  -  S3
  -  ClOUDFRONT
categories: 
  - HEXO
---

## 前言

這篇文章記錄一下如何將 hexo deploy 到 s3 當作靜態網站使用，這邊我使用的是 hexo + minos theme ， 並且先前已經使用了 s3 建立好 bucket 且搭配 CloudFront 來做 cdn 。

<!--more-->
## 建立權限

首先到 IAM 服務裡面新增 user，並且提供 S3 的權限，拿到 access key 跟  access key id。

## 設定 AWS 環境變數

將拿到的 access key 跟  access key id 設定在環境變數，以我使用 mac 舉例，會先建立 aws 的 config 檔案。

```bash
mkdir ~/.aws
touch config
```

接著將這些存入 config

```text
[default]
region=ap-northeast-1 --> 這個是我的要找到自己的設定
output=json
```

然後再建立 credentials

```bash
touch ~/.aws/credentials
```

接下來輸入

```text
[default]
aws_access_key_id=剛剛的 key id
aws_secret_access_key=剛剛的 key
```

## HEXO Deploy 設定

接著到 `hexo/_config.yml` 設定 deploy

```yaml
deploy:
  type: aws-s3
  bucket: bucket name
  region: ap-northeast-1
```

然後安裝 `hexo-deployer-aws-s3`

```bash
npm i -D hexo-deployer-aws-s3
```

接著就可以執行 `hexo d` 部署。
