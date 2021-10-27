# Docker OSWP ZAP環境

# Requirement
* [docker](https://www.docker.com/)

# Install
`.env.example` をコピー `.env` を作成。
各種設定値を修正。

Docker起動
```
docker-compose up -d --build
```

# Usage

## コンテナに入る
```
docker exec -it zap sh
docker exec -it webgoat sh
```

## WebGoat
WebGoat画面
http://localhost:8080/WebGoat/login

## ZAP
HUDプラグインが邪魔をするため，アンインストール
```
docker exec -it zap zap.sh -cmd -addonuninstall hud
```

WebSwing画面起動
http://localhost:8090/
```
docker exec -it zap zap-webswing.sh
```

ZAP Baseline Scan（レポートファイル出力）
[ZAP - Baseline Scan | OWASP ZAP](https://www.zaproxy.org/docs/docker/baseline-scan/)
実際の攻撃はなし
```
docker exec -it zap zap-baseline.py -t http://webgoat:8080/WebGoat/login -r report.html
```

ZAP Full Scan（レポートファイル出力）
[ZAP - Baseline Scan | OWASP ZAP](https://www.zaproxy.org/docs/docker/baseline-scan/)
実際に攻撃を行う
```
docker exec -it zap zap-full-scan.py -t http://webgoat:8080/WebGoat/login -r report.html
```


ZAP API Scan（レポートファイル出力）
[ZAP - Baseline Scan | OWASP ZAP](https://www.zaproxy.org/docs/docker/baseline-scan/)
実際に攻撃を行う
```
docker exec -it zap zap-api-scan.py -t http://webgoat:8080/WebGoat/login -r report.html
```

# Note
* [WebGoat/WebGoat: WebGoat is a deliberately insecure application](https://github.com/WebGoat/WebGoat)
* [Docker Hub webgoat/webgoat-8.0](https://hub.docker.com/r/webgoat/webgoat-8.0/)
* [ZAP Docker Documentation](https://www.zaproxy.org/docs/docker/)
* [Docker版OWASP ZAPを動かしてみる - Qiita](https://qiita.com/koujimatsuda11/items/83558cd62c20141ebdda)
* [DockerでOWASP ZAPを使う - みーのぺーじ](https://pc.atsuhiro-me.net/entry/2019/08/19/011324)
* [Docker版OWASP ZAPを使用してWebアプリの簡易的な脆弱性診断をしてみた](https://dev.classmethod.jp/articles/easy-vulnerability-diagnosis-of-web-app-with-owasp-zap-on-docker/)

# Author
* [こぴぺたん](https://twitter.com/c_a_p_engineer)

# License
[MIT license](https://en.wikipedia.org/wiki/MIT_License).
