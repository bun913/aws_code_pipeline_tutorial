# AWSコードシリーズの練習

CodePipelineのチュートリアルの実践してみました。

https://docs.aws.amazon.com/ja_jp/codepipeline/latest/userguide/tutorials-simple-codecommit.html

## CodeCommitリポジトリの作成

1. まずはコンソールからCodeCommitリポジトリを作成する。
   1. リポジトリ名をTestCodePipelineとする
![レポジトリ名](images/01_reponame.png)
2. IAMユーザーの認証情報を設定
   1. 上記画面にも記載されている通り、CodeCommtにアクセスするためのIAMユーザー設定を行う
   2. ユーザーにCodeCommitへのSSHアクセスのためのキーアップロード等が必要
      1. Macであれば `ssh-keygen` コマンドでキーペアを作成
      2.  `cat ~/.ssh/キー名 | pbocpy` でクリップボードに公開鍵情報をコピー
      3.  Iamユーザーの「認証情報」タブからSSHパブリックキーのアップロードを行っておく
          1.  このあたりの詳しいやり方は以下を参照
          2. 公式:https://docs.aws.amazon.com/ja_jp/codecommit/latest/userguide/setting-up-gc.html?icmpid=docs_acc_console_connect_np
          3. 毎度おなじみdevelopers.io:https://dev.classmethod.jp/articles/codecommit-try/
      4. ~/.ssh/configに記載する `User`はIAMユーザー名ではないので注意
![ssh設定](images/02_ssh_user.png)
   3. 以下のようにメッセージが出たらcloneできている
   4. 公式から取得したCodeDeployサンプル用のファイル一式をプロジェクトルートに設置
      1. https://docs.aws.amazon.com/ja_jp/codepipeline/latest/userguide/samples/SampleApp_Linux.zip

```
Cloning into 'TestCodePipeline'...
warning: You appear to have cloned an empty repository.
```
