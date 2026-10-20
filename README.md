
<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>PK Rakip Puanı</title>
<style>
*{box-sizing:border-box}
body{
  margin:0;min-height:100vh;display:grid;place-items:center;
  background:#0b0712;color:white;
  font-family:Arial,sans-serif;padding:20px
}
.panel{
  width:100%;max-width:400px;padding:25px;
  border:1px solid #7835a9;border-radius:22px;
  background:linear-gradient(145deg,#21102e,#100b19);
  box-shadow:0 0 35px #7c3aed25;text-align:center
}
.tag{color:#d8b4fe;font-size:12px;letter-spacing:2px}
h1{font-size:23px;margin:12px 0 24px}
.avatar{
  width:65px;height:65px;border-radius:50%;
  margin:auto;background:#3b1d54;
  display:grid;place-items:center;font-size:30px
}
.name{color:#d8b4fe;margin:14px 0 5px}
.score{font-size:clamp(35px,10vw,48px);font-weight:800;
  margin:8px 0;color:#fff}
.caption{font-size:12px;color:#b9a9c9}
input{
  display:block;width:100%;padding:13px;margin-top:20px;
  border:1px solid #58336e;border-radius:10px;
  background:#100b19;color:white;font-size:17px
}
button{
  width:100%;padding:13px;margin-top:12px;
  border:0;border-radius:10px;background:#a855f7;
  color:white;font-size:15px;font-weight:bold
}
.note{font-size:12px;line-height:1.6;color:#b9a9c9;margin-top:18px}
</style>
</head>
<body>
<main class="panel">
  <div class="tag">LIVE PK ASSISTANT</div>
  <h1>Rakip Puan Takibi</h1>
  <div class="avatar">🎮</div>
  <div class="name">RAKİP</div>
  <div class="score" id="score">0</div>
  <div class="caption">PUAN</div>

  <input id="points" type="number" min="0"
         step="1" placeholder="Rakibin puanını gir">
  <button id="update">Puanı Güncelle</button>

  <div class="note" id="message">
    Manuel puan girişi · Gerçek TikTok verisi bağlı değil
  </div>
</main>
<script>
const points = document.getElementById("points");
const score = document.getElementById("score");
const message = document.getElementById("message");

document.getElementById("update").addEventListener("click", () => {
  const value = points.value.trim();

  if (value === "" || !Number.isSafeInteger(Number(value)) ||
      Number(value) < 0) {
    message.textContent = "Lütfen geçerli bir puan gir.";
    return;
  }

  score.textContent = Number(value).toLocaleString("tr-TR");
  message.textContent = "Puan elle güncellendi; TikTok'a bağlı değil.";
});
</script>
</body>
</html>
