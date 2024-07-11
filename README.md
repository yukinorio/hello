```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Grafana Variable Update</title>
</head>
<body>
    <h1>Update Grafana Variable</h1>
    <iframe id="grafanaFrame" src="http://YOUR_GRAFANA_URL/d/YOUR_DASHBOARD_UID" width="100%" height="600"></iframe>
    <button onclick="updateGrafanaVariable('varName', 'varValue')">Update Variable</button>

    <script>
        function updateGrafanaVariable(varName, varValue) {
            const iframe = document.getElementById('grafanaFrame');

            // Check if the iframe content is accessible
            if (iframe.contentWindow && iframe.contentWindow.angular) {
                const contentWindow = iframe.contentWindow;

                try {
                    const varService = contentWindow.angular
                      .element('grafana-app')
                      .injector()
                      .get('variableSrv');

                    const dashboard = contentWindow.angular
                      .element('grafana-app')
                      .injector()
                      .get('dashboardSrv').dashboard;

                    const v = varService.templateSrv.variables.find(
                      ({ name }) => name === varName
                    );

                    if (!!v) {
                      varService.setOptionAsCurrent(v, { text: varValue, value: varValue });
                      varService.variableUpdated(v, false); // false to update manually via dashboard object

                      dashboard.templateVariableValueUpdated();
                      dashboard.startRefresh();
                    } else {
                      console.error('Variable not found');
                    }
                } catch (error) {
                    console.error('Error accessing AngularJS services:', error);
                }
            } else {
                console.error('Cannot access iframe content or AngularJS');
            }
        }
    </script>
</body>
</html>



```
