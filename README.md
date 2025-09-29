export default async function handler(req, res) {
  // 设置CORS头
  res.setHeader('Access-Control-Allow-Origin', '*');
  res.setHeader('Access-Control-Allow-Methods', 'GET, POST, OPTIONS');
  res.setHeader('Access-Control-Allow-Headers', 'Content-Type');
  
  // 处理预检请求
  if (req.method === 'OPTIONS') {
    return res.status(200).end();
  }
  
  try {
    // 目标API地址 - 替换为你的网站B地址
    const targetUrl = 'https://www.dy558dy.shop/data';
    
    // 转发请求到网站B
    const response = await fetch(targetUrl);
    const data = await response.json();
    
    // 返回网站B的数据
    res.status(200).json(data);
    
  } catch (error) {
    res.status(500).json({ error: 'Proxy error' });
  }
}
