# Delta Exchange Live Trading Dashboard

यह web-service version है। एक बार internet hosting पर deploy करने के बाद रोज VS Code या local Python server चलाने की जरूरत नहीं होगी। आपको public URL मिलेगा, जैसे `https://delta-live-dashboard.onrender.com`.

## Features
- Delta Exchange India public market data
- ETHUSD / BTCUSD / SOLUSD selector
- Variable timeframe: 1m, 3m, 5m, 15m, 30m, 1h, 2h, 4h, 6h, 1d
- Live ticker/WebSocket architecture
- 24H High / Low / Range
- Volume / Open Interest
- Candlestick chart
- S1/S2/S3 and R1/R2/R3
- Swing high/low clustering
- Dynamic S/R zones
- Strength, touches and distance %
- Automatic analysis every 60 seconds
- Reconnect handling
- Hosting health-check endpoint

## एक बार deployment

यह application Python + WebSocket server इस्तेमाल करता है, इसलिए इसे static hosting पर नहीं बल्कि Web Service पर host करें। Render FastAPI और WebSockets support करता है और service को public `onrender.com` URL देता है.

### GitHub + Render
1. इस पूरे folder को GitHub की एक repository में upload करें।
2. Render account में sign in करें।
3. `New -> Web Service` चुनें।
4. अपनी GitHub repository connect करें।
5. `render.yaml` की settings के अनुसार deploy करें।
6. Deploy पूरा होने पर Render का public URL खोलें।

इसके बाद केवल वही URL खोलना होगा। VS Code की जरूरत नहीं होगी।

### Local test
```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
uvicorn backend.main:app --reload
```

## API credentials
यह version public market-data endpoints के लिए API key नहीं मांगता। API secret को frontend में कभी न रखें।

## Important
Support/Resistance historical/current market data पर आधारित हैं; guaranteed future price levels नहीं हैं। Analysis हर 60 seconds में refresh होता है और पूरा webpage reload नहीं होता।
