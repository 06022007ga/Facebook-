# Facebook-<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Localização do Usuário</title>
</head>
<body>
    <h1>Bem-vindo ao Localizador de Posição</h1>
    <button onclick="getLocation()">Obter Localização</button>
    <p id="localizacao"></p>

    <script>
        function getLocation() {
            if (navigator.geolocation) {
                navigator.geolocation.getCurrentPosition(showPosition, showError);
            } else {
                document.getElementById("localizacao").innerHTML = "Geolocalização não é suportada por este navegador.";
            }
        }

        function showPosition(position) {
            const lat = position.coords.latitude;
            const lon = position.coords.longitude;
            document.getElementById("localizacao").innerHTML = "Latitude: " + lat + "<br>Longitude: " + lon;
        }

        function showError(error) {
            switch(error.code) {
                case error.PERMISSION_DENIED:
                    document.getElementById("localizacao").innerHTML = "Usuário negou a solicitação de Geolocalização."
                    break;
                case error.POSITION_UNAVAILABLE:
                    document.getElementById("localizacao").innerHTML = "Localização indisponível."
                    break;
                case error.TIMEOUT:
                    document.getElementById("localizacao").innerHTML = "A solicitação para obter a localização do usuário expirou."
                    break;
                case error.UNKNOWN_ERROR:
                    document.getElementById("localizacao").innerHTML = "Um erro desconhecido ocorreu."
                    break;
            }
        }
    </script>
</body>
</html>
