<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Genesys Widget Test</title>
    
    <script type="text/javascript">
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
        deploymentId: '8ca0bda5-1cde-483b-a844-32375da60f03'
      });
    </script>
</head>
<body>
    <h1>Genesys Integration</h1>
    <p>If the deployment ID and environment are active, the Genesys chat widget should appear on this page.</p>
</body>
</html>
