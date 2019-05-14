# linebotをherokuにデプロイするまとめ
## 前提
- herokuへの登録

## step0
ソースコードの最終行を以下のように修正

```python
if __name__ == "__main__":
  # app.run()
  port = int(os.getenv("PORT", 5000))
  app.run(host="0.0.0.0", port=port)
```

## step1
- herokuの`python`を選択
- Download the Heroku CLI for MacOSをクリックしてダウンロード。
  - ダウンロードしたファイルをダブルクリックしてインストールを進めます。

## step2
- `$ heroku login`
    -> 色々入力
- `$ heroku create <application name>`

## step3
必要ファイルの作成
```python
# runtime.txt pythonのバージョンを記載
python-3.7.2
```

```
# requirements.txt 必要ライブラリの記載
Flask==0.12.2
line-bot-sdk==1.5.0
```

```
#Procfile プログラムの実行方法を定義
web: python main.py
```

`$ git init`
`$ git add .`
`$ git commit -m "first commit"`
`$ git push heroku master`

## ログの出し方
`$ heroku logs --tail -a <application name>`
