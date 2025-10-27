<!doctype html>
<html lang="id">
<head>
<meta charset="utf-8" />
<meta name="viewport" content="width=device-width,initial-scale=1" />
<title>Pro Player Training Simulator</title>
<style>
  :root{
    --bg:#0b0f14;
    --panel:#0f1720;
    --accent:#12b886;
    --muted:#98a0ad;
    --danger:#ff5252;
    --glass: rgba(255,255,255,0.03);
  }
  html,body{height:100%;margin:0;font-family:Inter,ui-sans-serif,system-ui,Segoe UI,Roboto,"Helvetica Neue",Arial;}
  body{background:linear-gradient(180deg,#071019 0%, #0b1220 100%);color:#e6eef6;display:flex;align-items:stretch;padding:18px;box-sizing:border-box;}
  .container{flex:1;display:grid;grid-template-columns:1fr 340px;gap:16px;height:calc(100vh - 36px);}
  /* Left: game */
  .game-card{background:var(--panel);border-radius:12px;padding:12px;box-shadow:0 10px 30px rgba(2,6,23,0.6);display:flex;flex-direction:column;overflow:hidden}
  header.h{display:flex;gap:12px;align-items:center;padding:6px 8px}
  .title{font-weight:600;font-size:18px}
  .sub{color:var(--muted);font-size:13px}
  .stage{flex:1;display:flex;gap:12px;align-items:stretch}
  .viewport{flex:1;background:linear-gradient(180deg,#071826,#03101a);border-radius:10px;position:relative;overflow:hidden}
  canvas{display:block;width:100%;height:100%;background:transparent}
  .hud{position:absolute;left:12px;top:12px;display:flex;flex-direction:column;gap:8px}
  .hud .box{background:var(--glass);padding:6px 8px;border-radius:8px;font-size:13px;color:#dbeaf1}
  .crosshair{position:absolute;left:50%;top:50%

