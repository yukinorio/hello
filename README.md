```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grafana Dashboard Time Range Update</title>
</head>
<body>
    <h1>Grafana Dashboard</h1>
    <iframe id="grafanaFrame" src="http://YOUR_GRAFANA_URL/d/YOUR_DASHBOARD_UID" width="100%" height="600"></iframe>
    <h2>Update Grafana Dashboard Time Range</h2>
    <button onclick="updateDashboardTimeRange()">Update Time Range</button>
    <p id="message"></p>

    <script>
        const dashboardUid = 'YOUR_DASHBOARD_UID';
        const apiUrl = `http://YOUR_GRAFANA_URL/api/dashboards/uid/${dashboardUid}`;
        const apiKey = 'YOUR_API_KEY';

        function updateDashboardTimeRange() {
            fetch(apiUrl, {
                method: 'GET',
                headers: {
                    'Content-Type': 'application/json',
                    'Authorization': `Bearer ${apiKey}`
                }
            })
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                return response.json();
            })
            .then(data => {
                console.log('Dashboard data:', data);
                const dashboard = data.dashboard;

                // 新しい時間範囲を設定
                dashboard.time = {
                    from: 'now-12h', // 例: 12時間前から
                    to: 'now'        // 例: 現在まで
                };

                // 更新したダッシュボードデータを送信
                const updateApiUrl = `http://YOUR_GRAFANA_URL/api/dashboards/db`;
                
                return fetch(updateApiUrl, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                        'Authorization': `Bearer ${apiKey}`
                    },
                    body: JSON.stringify({
                        dashboard: dashboard,
                        overwrite: true
                    })
                });
            })
            .then(response => {
                if (!response.ok) {
                    throw new Error('Network response was not ok');
                }
                return response.json();
            })
            .then(data => {
                console.log('Dashboard updated:', data);
                document.getElementById('message').textContent = 'Dashboard time range updated successfully!';
                // ダッシュボードのiFrameをリロード
                const iframe = document.getElementById('grafanaFrame');
                iframe.src = iframe.src;
            })
            .catch(error => {
                console.error('Error updating dashboard:', error);
                document.getElementById('message').textContent = 'Failed to update dashboard time range.';
            });
        }
    </script>
</body>
</html>


```
