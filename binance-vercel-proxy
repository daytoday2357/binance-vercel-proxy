export default async function handler(req, res) {
  const target = req.query.url;
  if (!target || !target.startsWith("https://fapi.binance.com")) {
    return res.status(400).send("Missing or invalid 'url' parameter");
  }

  try {
    const response = await fetch(target, {
      headers: { 'User-Agent': 'Mozilla/5.0' }
    });
    const body = await response.text();
    res.setHeader("Access-Control-Allow-Origin", "*");
    res.setHeader("Content-Type", "application/json");
    res.status(200).send(body);
  } catch (err) {
    res.status(500).send("Error fetching target");
  }
}
