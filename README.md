<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Usuarios Avanzados</title>
    <style>
        /* Estilos Globales */
        body {
            font-family: 'Roboto', sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            box-sizing: border-box;
            background: linear-gradient(135deg, #8B4513, #FF8C00, #D2691E, #FF6347, #A0522D, #FFA500, #D2B48C, #FF7F50, 
            #FF1493, #FF6347, #00FF7F, #008080, #FFD700, #FF6347, #ADFF2F, #228B22, #8A2BE2, #7B68EE, 
            #FF4500, #FF6347, #00CED1, #5F9EA0, #4B0082, #9400D3, #FF6347, #FF0000, #00FA9A, #20B2AA, 
            #A52A2A, #FF7F50, #F08080, #FF6347, #800080, #4B0082, #48D1CC, #00CED1, #FFD700, #FF8C00, 
            #A9A9A9, #808080, #32CD32, #98FB98, #7FFF00, #32CD32, #FF00FF, #FF1493, #C71585, #FF1493, 
            #FF6347, #FF7F50, #FF4500, #228B22, #32CD32, #FFD700, #D2691E, #8B4513, #3CB371, #20B2AA, 
            #2E8B57, #3CB371, #00FF00, #006400, #BA55D3, #9932CC, #FF6347, #FF4500, #FFFF00, #FFD700, 
            #F0E68C, #BDB76B, #DC143C, #FF0000, #B22222, #FF6347, #800000, #8B0000, #2F4F4F, #008080, 
            #00BFFF, #1E90FF, #F5DEB3, #D2B48C, #F4A300, #F79C42, #C71585, #8B008B, #98FB98, #00FA9A, 
            #6495ED, #4169E1, #FF6347, #FF8C00, #4682B4, #5F9EA0, #800080, #8B008B, #FF8C00, #FF6347, 
            #D2691E, #8B4513, #DC143C, #FF0000, #ADFF2F, #9ACD32, #D8BFD8, #C71585, #9932CC, #8A2BE2, 
            #FF1493, #FF6347, #A52A2A, #B22222, #FF7F50, #FF6347, #FF0000, #8B0000, #5F9EA0, #20B2AA, 
            #FFD700, #FFFF00, #7FFF00, #32CD32, #800080, #9400D3, #C71585, #8B008B, #FF6347, #FF4500, 
            #B22222, #8B0000, #4B0082, #9932CC, #ADFF2F, #00FF00);
            transition: background 2s ease;
        }

        .container {
            background: rgba(255, 255, 255, 0.9);
            border-radius: 12px;
            box-shadow: 0 10px 30px rgba(0, 0, 0, 0.2);
            padding: 25px 40px;
            width: 100%;
            max-width: 850px;
            text-align: center;
            transition: transform 0.3s ease-in-out;
            overflow: hidden;
        }

        h1 {
            font-size: 2rem;
            color: #4e73df;
            font-weight: 700;
            margin-bottom: 15px;
            letter-spacing: 2px;
            text-transform: uppercase;
        }

        p {
            font-size: 1.1rem;
            color: #555;
            margin-bottom: 15px;
        }

        .info {
            background-color: #f7f8fa;
            padding: 15px;
            border-radius: 8px;
            margin-bottom: 15px;
            color: #4e73df;
            font-size: 1.05rem;
            box-shadow: 0 5px 15px rgba(0, 0, 0, 0.1);
            transition: transform 0.2s ease-in-out, box-shadow 0.2s ease;
        }

        table {
            width: 100%;
            border-collapse: collapse;
            margin-top: 30px;
            background-color: #fff;
            border-radius: 10px;
            font-size: 0.9rem;
        }

        th, td {
            padding: 8px 10px;
            text-align: left;
            border-bottom: 1px solid #ddd;
        }

        th {
            background-color: #4e73df;
            color: #fff;
            font-weight: bold;
            text-transform: uppercase;
        }

        td {
            background-color: #f9f9f9;
        }

        td:hover {
            background-color: #f1f7fc;
            transition: background-color 0.3s ease;
        }

        .logs-container {
            margin-top: 40px;
            overflow-y: auto;
            max-height: 400px;
        }

        .loader {
            font-size: 1.2rem;
            color: #888;
        }

        @media screen and (max-width: 768px) {
            .container {
                padding: 15px;
            }

            h1 {
                font-size: 1.6rem;
            }

            p, .info {
                font-size: 1rem;
            }
        }

        button {
            background-color: #4e73df;
            color: #fff;
            padding: 12px 20px;
            border: none;
            border-radius: 5px;
            font-size: 1.1rem;
            cursor: pointer;
            transition: background-color 0.3s ease;
        }

        button:hover {
            background-color: #355c8c;
        }

        button:active {
            background-color: #4e73df;
            transform: translateY(2px);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>Usuarios Avanzados</h1>
    
        <p id="saludo"></p>
        
        <div class="info" id="location-info">
            <div class="loader">Cargando ubicación...</div>
        </div>

        <div class="info" id="device-info">
            <div class="loader">Cargando información del dispositivo...</div>
        </div>

        <div class="info" id="dpi-info">
            <div class="loader">Cargando DPI...</div>
        </div>

        <div class="info" id="browser-info">
            <div class="loader">Cargando información del navegador...</div>
        </div>

        <div class="info" id="gpu-info">
            <div class="loader">Cargando información de la GPU...</div>
        </div>

        <div class="logs-container">
            <h3>Lista de Usuarios:</h3>
            <table id="logs-table">
                <thead>
                    <tr>
                        <th>Hora</th>
                        <th>Ubicación e IP</th>
                        <th>Dispositivo</th>
                        <th>DPI</th>
                        <th>Navegador</th>
                        <th>GPU</th>
                        <th>Sistema Operativo</th>
                        <th>Dispositivo de Entrada</th>
                        <th>Resolución</th>
                    </tr>
                </thead>
                <tbody id="logs"></tbody>
            </table>
        </div>
    </div>

    <script>
        // Obtener la ubicación usando IP
        async function obtenerUbicacion() {
            const apiURL = 'https://ipinfo.io/json';
            try {
                const response = await fetch(apiURL);
                const data = await response.json();
                const ip = data.ip || 'No disponible';
                const city = data.city || '';
                const region = data.region || '';
                const country = data.country || '';
                const locationText = city && region && country
                    ? `Estás ubicado en: <strong>${city}, ${region}, ${country}</strong> (IP: ${ip})`
                    : `IP: ${ip}`;
                document.getElementById('location-info').innerHTML = locationText;
                registrarUsuario(locationText);
            } catch (error) {
                document.getElementById('location-info').innerHTML = 'No se pudo obtener la ubicación.';
            }
        }

        // Registrar información del usuario
        function registrarUsuario(ubicacion) {
            const dpi = window.devicePixelRatio;
            const navegador = navigator.userAgent.includes('Chrome') ? 'Google Chrome' : 'Navegador desconocido';
            const gpu = 'Desconocida'; // Aquí podrías hacer más detección de GPU si lo deseas
            const os = navigator.platform;
            const entrada = 'Ratón o Pantalla táctil';
            const resolucion = `${screen.width} x ${screen.height}`; // Resolución de la pantalla

            const logsContainer = document.getElementById('logs');
            const logEntry = document.createElement('tr');
            const hora = new Date().toLocaleString();

            logEntry.innerHTML = `
                <td>${hora}</td>
                <td>${ubicacion}</td>
                <td>${navigator.userAgent}</td>
                <td>${dpi}</td>
                <td>${navegador}</td>
                <td>${gpu}</td>
                <td>${os}</td>
                <td>${entrada}</td>
                <td>${resolucion}</td>
            `;
            logsContainer.appendChild(logEntry);
        }

        obtenerUbicacion(); // Llamar al inicio
    </script>
</body>
</html>
