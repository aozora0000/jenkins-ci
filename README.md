# jenkins with Docker用CI環境構築ファイル郡

## 概要
JenkinsからDockerを利用してビルド・テスト環境を作成する為のDockerfileです。

内部でansibleを利用している為、ansibleからのイメージビルドは出来ないようです。

## 内容

### jenkins-ci-base
このイメージをベースにjenkins用のイメージをビルドします。

他のイメージからの依存がありますので、一番最初にビルドをしなければなりません。

```
docker build -t jenkins-ci-base ./jenkins-ci-base
```

### jenkins-ci-php
jenkins-ci-baseをベースにphpbrewをインストールしています。

また
- PHP 5.3.29
- PHP 5.4.36(default)
- PHP 5.5.20
- PHP 5.6.4

を並列コンパイル＆インストールします。

非常に負荷が高い為、他作業との並列進行はオススメ出来ません。
