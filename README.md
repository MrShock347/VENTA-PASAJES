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
            position: relative;
            min-height: 100vh;
        }
        
        body::before {
            content: '';
            background-image: url('https://d41chssnpqdne.cloudfront.net/user_upload_by_module/chat_bot/files/645820/aCp1oQ6CvZ1s0XIV.jpg?Expires=1741578333&Signature=QeY8P43SUE9S-R4gVTPMrSzgh5pD~LTlYID-trrs5zTnhQUL24bNqXLZfC9JGgZLHIeHdJGjERGAg~GD~GzGmMu~hyo-5X5tsaCOMOF3hzgtK~wxkr1HDqqjskGNPOfVcHpa34~vsKaS1uYNLpdJAUBm6QwgQqbMtUFLV83nCAHmBApWymt~vjOqwGo4DyZ73Qnv7T2e8BBcVTVgsG2BnfwStpg-0wgcDEU4C3Mp1VnZdBhLltSnBucDTbZab2U3twuyiXsak4g4~4~ekbdfzI5Mj4iQM-8msrPngE7XKJWvym75F-e96hZZeQ41ooyOMWlAwYxyzb43ImPwD9eecw__&Key-Pair-Id=K3USGZIKWMDCSX');
            background-size: cover;
            background-position: center;
            opacity: 0.3; /* Opacidad reducida */
            position: absolute;
            top: 0;
            left: 0;
            bottom: 0;
            right: 0;
            z-index: -1;
        }

        .container {
            max-width: 600px;
            margin: 100px auto;
            background: rgba(255, 255, 255, 0.95);
            padding: 30px;
            border-radius: 15px;
            box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
            position: relative;
        }

        input, button, select {
            width: 100%;
            padding: 12px;
            margin: 12px 0;
            border: 1px solid #ddd;
            border-radius: 8px;
            font-size: 16px;
            background: white;
        }

        button {
            background-color: #007bff;
            color: white;
            border: none;
            cursor: pointer;
            transition: background-color 0.3s;
            font-weight: bold;
        }

        button:hover {
            background-color: #0056b3;
        }

        select {
            appearance: none;
            -webkit-appearance: none;
            background-image: url("data:image/svg+xml;charset=UTF-8,%3csvg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 24 24' fill='none' stroke='currentColor' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'%3e%3cpolyline points='6 9 12 15 18 9'%3e%3c/polyline%3e%3c/svg%3e");
            background-repeat: no-repeat;
            background-position: right 1rem center;
            background-size: 1em;
        }
    </style>
    <script>
        // Tu script completo se mantiene igual
        document.addEventListener("DOMContentLoaded", function() {
            let today = new Date().toISOString().split('T')[0];
            document.getElementById("fecha-vuelo").setAttribute("min", today);
            document.getElementById("fecha-regreso").setAttribute("min", today);
            document.getElementById("fecha-regreso").style.display = "none";

            document.getElementById("tipo-viaje").addEventListener("change", function() {
                if (this.value === "Ida y vuelta") {
                    document.getElementById("fecha-regreso").style.display = "block";
                } else {
                    document.getElementById("fecha-regreso").style.display = "none";
                }
            });

            document.getElementById("fecha-vuelo").addEventListener("change", function() {
                let fechaIda = document.getElementById("fecha-vuelo").value;
                let fechaRegreso = document.getElementById("fecha-regreso");
                fechaRegreso.setAttribute("min", fechaIda);
                if (fechaRegreso.value < fechaIda) {
                    fechaRegreso.value = fechaIda;
                }
            });
        });

        function enviarAWhatsApp() {
            let origen = document.getElementById("origen").value;
            let destino = document.getElementById("destino").value;
            let tipoViaje = document.getElementById("tipo-viaje").value;
            let aerolinea = document.getElementById("aerolinea").value;
            let fechaIda = document.getElementById("fecha-vuelo").value;
            let fechaRegreso = document.getElementById("fecha-regreso").value;
            let pasajeros = document.getElementById("pasajeros").value;
            
            if (!origen || !destino || !tipoViaje || !aerolinea || !fechaIda || !pasajeros || (tipoViaje === "Ida y vuelta" && !fechaRegreso)) {
                alert("Por favor, complete todos los campos antes de continuar.");
                return;
            }

            let mensaje = `Hola, quiero comprar un pasaje:\n- Origen: ${origen}\n- Destino: ${destino}\n- Tipo de viaje: ${tipoViaje}\n- Aerolínea: ${aerolinea}\n- Fecha de ida: ${fechaIda}`;
            
            if (tipoViaje === "Ida y vuelta") {
                mensaje += `\n- Fecha de regreso: ${fechaRegreso}`;
            }
            
            mensaje += `\n- Pasajeros: ${pasajeros}`;
            
            let numerosWhatsApp = ["51949725382", "51963888979"];
            let numeroWhatsApp = numerosWhatsApp[Math.floor(Math.random() * numerosWhatsApp.length)];
            let url = `https://wa.me/${numeroWhatsApp}?text=${encodeURIComponent(mensaje)}`;
            window.location.href = url;
        }
    </script>
</head>
<body>
    <!-- Todo tu HTML se mantiene igual -->
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
