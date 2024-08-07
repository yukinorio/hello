```
server {
    ...

    location /grafana/ {
        proxy_pass http://localhost:3000;
        proxy_set_header Authorization "Bearer your_api_key";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }

    ...
}



Grafana ver11.1.0
■iframe認証
解決策かも？
https://github.com/grafana/grafana/issues/3752

解決策っぽい
https://grafana.com/docs/grafana/latest/setup-grafana/configure-security/configure-authentication/jwt/#iframe-embedding

iframeを埋め込んでnginxのリバースプロキシで認証する方法を教えて（未解決、2022年）
https://community.grafana.com/t/grafana-dashboards-on-iframe-and-reverse-proxy-with-auth-proxy/74484

iframeで埋め込んだgrafanaにリバースプロキシで認証して表示する方法を教えて（未解決、2024年）
https://community.grafana.com/t/authenticating-grafana-in-an-iframe-via-reverse-proxy/119919

iframeで埋め込んだgrafanaにリバースプロキシで認証する方法を教えて（回答なし、2024年）
https://community.grafana.com/t/auth-grafana-with-reverse-proxy-in-iframe-for-html-or-with-axios-http-in-nodejs-express/120095

iframeで埋め込んだGrafanaに認証したい（未解決、2021年）
https://stackoverflow.com/questions/69299445/allow-grafana-charts-iframe-to-only-be-accessed-through-trusted-domain

iframeで埋め込まれたGrafanaの認証方法はある？この質問ってよく出るけど誰も解決してないよ（未解決、2022年）
https://community.grafana.com/t/forward-authentication-to-grafana-embedded-in-an-iframe/70295

iframeのGrafanaで自動ログインをしたい（回答あり、2017年）
https://stackoverflow.com/questions/45230407/auto-login-to-grafana-from-web-application-using-credentials-or-token

■iframe
irfame全体の読み込みを防止したい（回答なし）
https://community.grafana.com/t/prevent-full-iframe-reloading-when-variable-changed-for-grafana-url/33933

iframeのsrcを変更した時に画面が更新されない方法はあるか？（未解決）
https://community.grafana.com/t/prevent-iframe-from-reloading-when-a-variable-passed-as-a-parameter-is-updated/29799

リロードせずにレンジは変更できるか（回答なし）
https://community.grafana.com/t/how-to-change-a-embeded-grafana-page-s-timerange-without-reload/41287

iframeのパネルをスムーズに操作したい（回答なし。AngularやReactで解決できるという話題がある）
https://community.grafana.com/t/how-can-i-interact-with-shared-panel-by-vue-js/38647

ダッシュボードにある時間範囲の変更を埋め込むことはできるか？（回答なし）
https://community.grafana.com/t/embed-common-time-range-controls-in-iframe-with-dashboard/31258

リロードせずにレンジを変更できるか？（回答なし）
https://community.grafana.com/t/how-to-change-a-embeded-grafana-page-s-timerange-without-reload/41287

■解決策？
Angularで書き換える（今はReactだから微妙に使えないかも）
https://community.grafana.com/t/interact-with-embedded-dashboards/3408

■postMessage
postMessageを使って書き換えられないか（回答なし）
https://community.grafana.com/t/support-for-navigating-an-embedded-grafana-using-postmessage/48459

■Angular
TimePickerの操作方法
https://stackoverflow.com/questions/52070668/calling-grafana-angular-timepickerctrl-function-from-javascript


■iframeの連携は無理？（Timepickerを操作できるか？）
https://community.grafana.com/t/timepicker-for-iframe-panels/2285/2


■その他
HTMLパネルの更新
https://community.grafana.com/t/html-panel-refresh/4031
```
