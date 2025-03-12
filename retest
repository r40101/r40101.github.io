const express = require('express');
const bodyParser = require('body-parser');
const app = express();

app.use(bodyParser.json());

app.post('/receber-localizacao', (req, res) => {
    const { latitude, longitude } = req.body;
    console.log(`Localização recebida: Latitude ${latitude}, Longitude ${longitude}`);
    res.json({ success: true });
});

app.listen(3000, () => {
    console.log('Servidor rodando na porta 3000');
});
