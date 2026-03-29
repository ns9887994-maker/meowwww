const express = require('express');
const cors = require('cors');
const axios = require('axios');

const app = express();
app.use(cors());
app.use(express.json());

app.post('/api/get-video', async (req, res) => {
    const videoUrl = req.body.url;
    if (!videoUrl) return res.status(400).json({ error: "No link!" });

    const options = {
        method: 'GET',
        url: 'https://social-download-all-in-one.p.rapidapi.com/v1/social/autolink',
        params: { url: videoUrl },
        headers: {
            'x-rapidapi-key': 'YOUR_ACTUAL_API_KEY_HERE', // Yahan apni key daalein
            'x-rapidapi-host': 'social-download-all-in-one.p.rapidapi.com'
        }
    };

    try {
        const response = await axios.request(options);
        res.json({
            hd_link: response.data.url || response.data.links[0].url
        });
    } catch (error) {
        res.status(500).json({ error: "API Error" });
    }
});

const PORT = process.env.PORT || 3000;
app.listen(PORT, () => console.log(`Server running on ${PORT}`));