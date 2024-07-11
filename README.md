<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grafana API Control</title>
    <script>
        const apiKey = 'YOUR_API_KEY';  // Replace with your Grafana API key

        async function updateTimeRange(from, to) {
            const iframe = document.getElementById("grafanaFrame");
            const src = new URL(iframe.src);
            src.searchParams.set('from', from);
            src.searchParams.set('to', to);
            iframe.src = src.toString();
        }
    </script>
</head>
<body>
    <iframe id="grafanaFrame" src="http://your-grafana-url/d/your-dashboard-id" width="100%" height="600"></iframe>
    <br>
    <button onclick="updateTimeRange('now-1h', 'now')">Last 1 Hour</button>
    <button onclick="updateTimeRange('now-6h', 'now')">Last 6 Hours</button>
    <button onclick="updateTimeRange('now-1d', 'now')">Last 24 Hours</button>
</body>
</html>
