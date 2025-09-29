export default async function handler(req, res) {

  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');
  
  if (req.method === 'OPTIONS') {
    return res.status(200).end();
  }
  
  try {
    const targetUrl = 'https://api.dy558dy.shop/data';
    
    const response = await fetch(targetUrl);
    const data = await response.json();
    
    res.status(200).json(data);
    
  } catch (error) {
    res.status(500).json({ error: 'Proxy error' });
  }
}
