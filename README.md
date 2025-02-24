<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Venta de Pasajes</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            text-align: center;
            background: url('desktop-background.jpg') no-repeat center center fixed;
            background-size: cover;
        }
        @media (max-width: 768px) {
            body {
                background: url('mobile-background.jpg') no-repeat center center fixed;
                background-size: cover;
            }
        }
        .container {
            max-width: 600px;
            margin: 100px auto;
            background: rgba(255, 255, 255, 0.8);
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0 0 15px rgba(0, 0, 0, 0.2);
        }
        input, button, select {
            width: 100%;
            padding: 10px;
            margin: 10px 0;
            border: 1px solid #ccc;
            border-radius: 5px;
        }
        button {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
        }
        button:hover {
            background-color: #0056b3;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>TOURS TRAVELS LA SOLUCIÓN</h1>
        <form onsubmit="event.preventDefault(); enviarAWhatsApp();">
            <select id="origen" required>
                <option value="" disabled selected>Selecciona el origen</option>
                <option value="Lima">Lima - Aeropuerto Jorge Chávez</option>
                <option value="Arequipa">Arequipa - Aeropuerto Rodríguez Ballón</option>
                <option value="Cusco">Cusco - Aeropuerto Alejandro Velasco Astete</option>
                <option value="Trujillo">Trujillo - Aeropuerto Capitán FAP Carlos Martínez de Pinillos</option>
                <option value="Piura">Piura - Aeropuerto Capitán FAP Guillermo Concha Iberico</option>
                <option value="Chiclayo">Chiclayo - Aeropuerto Capitán FAP José A. Quiñones</option>
                <option value="Iquitos">Iquitos - Aeropuerto Coronel FAP Francisco Secada Vignetta</option>
                <option value="Tacna">Tacna - Aeropuerto Coronel FAP Carlos Ciriani Santa Rosa</option>
                <option value="Juliaca">Juliaca - Aeropuerto Inca Manco Cápac</option>
                <option value="Pucallpa">Pucallpa - Aeropuerto Capitán FAP David Abensur Rengifo</option>
                <option value="Tarapoto">Tarapoto - Aeropuerto Cadete FAP Guillermo del Castillo Paredes</option>
            </select>
            <select id="destino" required>
                <option value="" disabled selected>Selecciona el destino</option>
                <option value="Lima">Lima - Aeropuerto Jorge Chávez</option>
                <option value="Arequipa">Arequipa - Aeropuerto Rodríguez Ballón</option>
                <option value="Cusco">Cusco - Aeropuerto Alejandro Velasco Astete</option>
                <option value="Trujillo">Trujillo - Aeropuerto Capitán FAP Carlos Martínez de Pinillos</option>
                <option value="Piura">Piura - Aeropuerto Capitán FAP Guillermo Concha Iberico</option>
                <option value="Chiclayo">Chiclayo - Aeropuerto Capitán FAP José A. Quiñones</option>
                <option value="Iquitos">Iquitos - Aeropuerto Coronel FAP Francisco Secada Vignetta</option>
                <option value="Tacna">Tacna - Aeropuerto Coronel FAP Carlos Ciriani Santa Rosa</option>
                <option value="Juliaca">Juliaca - Aeropuerto Inca Manco Cápac</option>
                <option value="Pucallpa">Pucallpa - Aeropuerto Capitán FAP David Abensur Rengifo</option>
                <option value="Tarapoto">Tarapoto - Aeropuerto Cadete FAP Guillermo del Castillo Paredes</option>
            </select>
            <select id="tipo-viaje" required>
                <option value="" disabled selected>Tipo de viaje</option>
                <option value="Ida">Solo ida</option>
                <option value="Ida y vuelta">Ida y vuelta</option>
            </select>
            <input type="date" id="fecha-vuelo" required>
            <input type="date" id="fecha-regreso" required>
            <select id="aerolinea" required>
                <option value="" disabled selected>Selecciona la aerolínea</option>
                <option value="LATAM">LATAM</option>
                <option value="SKY">SKY</option>
                <option value="STAR PERÚ">STAR PERÚ</option>
            </select>
            <input type="number" id="pasajeros" placeholder="Cantidad de pasajeros" min="1" required>
            <button type="submit">Buscar Pasajes</button>
        </form>
    </div>
</body>
</html>
