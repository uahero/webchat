<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    
    <meta name="robots" content="noindex, nofollow">
    
    <title>Genesys Deployment Test Tool</title>
    <style>
        body { font-family: sans-serif; padding: 20px; }
        .control-panel { margin: 20px 0; padding: 15px; border: 1px solid #ccc; background: #f9f9f9; display: inline-block; }
        input[type="text"] { padding: 8px; width: 300px; margin-right: 10px; }
        button { padding: 8px 16px; cursor: pointer; }
    </style>
</head>
<body>
    <h1>Genesys Integration</h1>
    
    <p>This is the deployment test tool for the USE1 region.</p>

    <div class="control-panel">
        <label for="deploymentInput"><strong>Deployment ID:</strong></label><br><br>
        <input type="text" id="deploymentInput" placeholder="Enter your Deployment ID">
        <button onclick="reloadWidget()">Proceed</button>
    </div>

    <script type="text/javascript">
        // 1. Function to check if a Deployment ID is in the URL
        function getQueryParam(param) {
            const urlParams = new URLSearchParams(window.location.search);
            return urlParams.get(param);
        }

        // 2. Set the default ID or grab the one from the URL
        const defaultDeploymentId = '01e23757-278e-4b5e-9bd6-ab4af20ad1c6';
        const activeDeploymentId = getQueryParam('deploymentId') || defaultDeploymentId;

        // 3. Populate the input field so the user sees what is currently active
        document.getElementById('deploymentInput').value = activeDeploymentId;

        // 4. Function to reload the page with the new deployment ID
        function reloadWidget() {
            const newId = document.getElementById('deploymentInput').value.trim();
            if (newId) {
                // Reloads the page with the new ID in the query string to guarantee a clean widget load
                window.location.href = window.location.pathname + '?deploymentId=' + encodeURIComponent(newId);
            } else {
                alert("Please enter a valid Deployment ID.");
            }
        }

        // 5. Inject the Genesys snippet using the active Deployment ID
        if (activeDeploymentId) {
            console.log("Loading Genesys widget for deployment:", activeDeploymentId);
            (function (g, e, n, es, ys) {
                g['_genesysJs'] = e;
                g[e] = g[e] || function () {
                (g[e].q = g[e].q || []).push(arguments)
                };
                g[e].t = 1 * new Date();
                g[e].c = es;
                ys = document.createElement('script'); ys.async = 1; ys.src = n; ys.charset = 'utf-8'; document.head.appendChild(ys);
            })(window, 'Genesys', 'https://apps.mypurecloud.com/genesys-bootstrap/genesys.min.js', {
                environment: 'prod',
                deploymentId: activeDeploymentId
            });
        }
    </script>
</body>
</html>
