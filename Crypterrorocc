<!DOCTYPE html>
<html lang="it">
<head>
   <meta charset="UTF-8">
   <meta name="viewport" content="width=device-width, initial-scale=1.0">
   <meta http-equiv="X-UA-Compatible" content="ie=edge">
   <title>Rileva IP tramite WebRTC</title>
   <style>
       body {
           font-family: Arial, sans-serif;
           text-align: center;
           margin-top: 50px;
       }
       #result {
           margin-top: 20px;
           padding: 10px;
           border: 1px solid #ccc;
           display: inline-block;
           background-color: #f9f9f9;
       }
   </style>
</head>
<body>

   <h1>Rilevazione IP tramite WebRTC</h1>
   <p>Qui sotto verranno visualizzati gli indirizzi IP rilevati:</p>
   <div id="result">
       <strong>Indirizzo IP:</strong> 
   </div>

   <script>
   async function getIPs() {
       let ipList = [];
       let pc = new RTCPeerConnection();

       // Crea un canale dati per far scattare la raccolta dei candidati ICE
       pc.createDataChannel("");

       // Crea un'offerta WebRTC e imposta la descrizione locale
       pc.createOffer().then(offer => pc.setLocalDescription(offer));

       // Intercetta i candidati ICE e raccoglie gli indirizzi IP
       pc.onicecandidate = (event) => {
           if (!event || !event.candidate) return; // Interrompe se non ci sono candidati ICE

           // Estrae l'IP dal candidato ICE
           let ip = event.candidate.candidate.split(' ')[4];

           // Evita duplicati
           if (!ipList.includes(ip)) {
               ipList.push(ip);
               document.getElementById("result").textContent += ` ${ip}`;
           }
       };
   }

   // Esegue la funzione quando la pagina è caricata
   window.onload = getIPs;
   </script>

</body>
</html>
