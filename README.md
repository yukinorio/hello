```
server {
    listen 80;
    server_name example.com;

    location / {
        proxy_pass http://localhost:8080;
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
    }
}



Grafana ver11.1.0

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
