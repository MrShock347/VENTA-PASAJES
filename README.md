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
            background-color: white;
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
        #fecha-regreso {
            display: none;
        }
    </style>
    <script>
        document.addEventListener("DOMContentLoaded", function() {
            let today = new Date().toISOString().split('T')[0];
            document.getElementById("fecha-vuelo").setAttribute("min", today);
            document.getElementById("fecha-regreso").setAttribute("min", today);

            document.getElementById("tipo-viaje").addEventListener("change", function() {
                let fechaRegreso = document.getElementById("fecha-regreso");
                if (this.value === "Ida y vuelta") {
                    fechaRegreso.style.display = "block";
                    fechaRegreso.required = true;
                } else {
                    fechaRegreso.style.display = "none";
                    fechaRegreso.required = false;
                    fechaRegreso.value = "";
                }
            });

            document.getElementById("fecha-vuelo").addEventListener("change", function() {
                let fechaRegreso = document.getElementById("fecha-regreso");
                fechaRegreso.setAttribute("min", this.value);
            });
        });

        function enviarAWhatsApp() {
            let origen = document.getElementById("origen").value;
            let destino = document.getElementById("destino").value;
            let tipoViaje = document.getElementById("tipo-viaje").value;
            let fecha = document.getElementById("fecha-vuelo").value;
            let fechaRegreso = document.getElementById("fecha-regreso").value;
            let pasajeros = document.getElementById("pasajeros").value;

            if (!origen || !destino || !tipoViaje || !fecha || !pasajeros) {
                alert("Por favor, complete todos los campos antes de continuar.");
                return;
            }

            let mensaje = `Hola, quiero comprar un pasaje:\n- Origen: ${origen}\n- Destino: ${destino}\n- Tipo de viaje: ${tipoViaje}\n- Fecha de ida: ${fecha}\n- Pasajeros: ${pasajeros}`;
            
            if (tipoViaje === "Ida y vuelta" && fechaRegreso) {
                mensaje += `\n- Fecha de regreso: ${fechaRegreso}`;
            }
            
            let numerosWhatsApp = ["51949725382", "51963888979"];
            let numeroWhatsApp = numerosWhatsApp[Math.floor(Math.random() * numerosWhatsApp.length)];
            let url = `https://wa.me/${numeroWhatsApp}?text=${encodeURIComponent(mensaje)}`;
            window.location.href = url;
        }
    </script>
</head>
<body>
    <div class="container">
        <h1>TOURS TRAVELS LA SOLUCIÓN</h1>
        <p>✈️ Bienvenido a TOURS TRAVELS LA SOLUCIÓN 🌍✨. Tu viaje comienza aquí, ofreciéndote los mejores pasajes con las aerolíneas más confiables. 🛫 Elige tu destino, selecciona tus fechas y prepárate para una experiencia sin preocupaciones. ¡Tu aventura empieza ahora! 🚀🎟️</p>
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
            <input type="date" id="fecha-vuelo" required>
            <input type="date" id="fecha-regreso" required>
            <input type="number" id="pasajeros" placeholder="Cantidad de pasajeros" min="1" required>
            <button type="submit">Buscar Pasajes</button>
        </form>
    </div>
</body>
</html>
