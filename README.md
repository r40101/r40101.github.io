<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Compartilhar Localização</title>
</head>
<body>
    <h1>Compartilhe sua localização atual</h1>
    <p>Clique no botão abaixo para compartilhar sua localização.</p>
    <button onclick="getLocation()">Compartilhar Localização</button>

    <script>
        function getLocation() {
            if (navigator.geolocation) {
                // Solicita a localização do usuário
                navigator.geolocation.getCurrentPosition(sendLocation, showError);
            } else {
                alert("Seu navegador não suporta geolocalização.");
            }
        }

        function sendLocation(position) {
            const latitude = position.coords.latitude;
            const longitude = position.coords.longitude;

            // Envia a localização para o servidor
            fetch(https://rece01.github.io/, {
                method: 'POST',
                headers: {
                    'Content-Type': 'application/json',
                },
                body: JSON.stringify({ latitude, longitude }),
            })
            .then(response => response.json())
            .then(data => {
                alert("Localização compartilhada com sucesso!");
            })
            .catch(error => {
                console.error('Erro ao enviar localização:', error);
            });
        }

        function showError(error) {
            switch(error.code) {
                case error.PERMISSION_DENIED:
                    alert("Você negou a permissão para compartilhar a localização.");
                    break;
                case error.POSITION_UNAVAILABLE:
                    alert("A localização não está disponível.");
                    break;
                case error.TIMEOUT:
                    alert("A solicitação de localização expirou.");
                    break;
                default:
                    alert("Ocorreu um erro ao obter a localização.");
            }
        }
    </script>
</body>
</html>
