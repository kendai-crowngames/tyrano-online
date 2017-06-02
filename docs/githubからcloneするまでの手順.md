# githubへのつなぎ方

## sshの設定

### 暗号鍵の設置

googleドライブの`sshkey/crowngames`ファイルを`~/.ssh`フォルダにコピーする。

#### ~/.sshフォルダが分からない場合

* gitbashを起動
* `pwd ~/.ssh`でフォルダのパスが分かる
* `cd ~/.ssh`でフォルダに移動してから`explorer .`でフォルダが開く。

### ホストの設定

`~/.ssh/config`ファイルに以下を追記

```
Host github.com.crowngames
  HostName github.com
  User git
  Port 22
  IdentityFile ~/.ssh/crowngames
  TCPKeepAlive yes
  IdentitiesOnly yes
```

## 認証情報の保存

### windowsの場合

キャッシュを有効にするコマンド

```
git config --global credential.helper wincred
```

認証情報の保存

```
git credential-wincred store
```

入力モードになるので、以下のように保存
`{user}`と`{pass}`は自分の環境に合わせて保存すること

```
protocol=ssh
host=github.com.crowngames
username={user}
password={pass}
``

## 参考

[Qiita-GitHubの複数アカウントを使い分けるならSSHよりhttpsの方がいいんじゃね？という話][*1]  
[Caching your GitHub password in Git][*2]
[ssh-agent][*3]


[*1]:http://qiita.com/zaki-yama/items/bfb0c2bef516af58c3fa
[*2]]:https://help.github.com/articles/caching-your-github-password-in-git/
[*3]:https://help.github.com/articles/working-with-ssh-key-passphrases/