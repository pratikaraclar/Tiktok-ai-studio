# Tiktok-ai-studio

<!DOCTYPE html>
<html lang="tr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#090711">
<title>TikTok AI Studio</title>
<style>
:root {
  --bg:#090711; --panel:#151020; --line:#30213f;
  --purple:#a855f7; --pink:#e879f9;
  --text:#f8f5ff; --muted:#b6a9c8;
}
* { box-sizing:border-box; }
body {
  margin:0; background:var(--bg); color:var(--text);
  font:15px/1.6 Arial,sans-serif;
}
header {
  padding:18px 5%; border-bottom:1px solid var(--line);
  display:flex; align-items:center; justify-content:space-between;
  gap:12px; background:#0d0915;
}
.logo { font-size:21px; font-weight:800; }
.logo span { color:var(--pink); }
.pill {
  border:1px solid #553277; border-radius:20px;
  color:#e9d5ff; padding:5px 10px; font-size:12px;
}
main { width:min(1000px,92%); margin:auto; }
.hero { padding:38px 0 24px; }
.eyebrow { color:var(--pink); font-size:13px; }
h1 { font-size:clamp(30px,6vw,46px); line-height:1.15; margin:10px 0; }
p { color:var(--muted); }
.grid {
  display:grid; grid-template-columns:repeat(2,minmax(0,1fr));
  gap:16px; padding-bottom:25px;
}
.card {
  min-width:0; padding:20px; border:1px solid var(--line);
  border-radius:16px; background:linear-gradient(145deg,#191126,#100c18);
}
.card h2 { font-size:18px; margin:0 0 5px; }
label { display:block; margin:13px 0 5px; font-size:13px; }
input,textarea,select {
  width:100%; border:1px solid var(--line); border-radius:9px;
  padding:12px; background:#0b0811; color:white; font:inherit;
}
textarea { min-height:85px; resize:vertical; }
button {
  border:0; border-radius:9px; padding:12px 15px;
  background:linear-gradient(100deg,#7c3aed,#c026d3);
  color:white; font-weight:bold; cursor:pointer;
}
.action { width:100%; margin-top:13px; }
.secondary {
  background:#241530; border:1px solid #68408c;
  margin-top:10px;
}
.output {
  margin-top:14px; padding:12px; background:#0b0811;
  border:1px solid #553277; border-radius:10px;
  white-space:pre-wrap; overflow-wrap:anywhere;
}
.hidden { display:none; }
.status { font-size:13px; color:#fcd34d; }
.metrics { display:grid; grid-template-columns:repeat(3,1fr); gap:10px; }
.metric {
  background:#100b18; border:1px solid var(--line);
  border-radius:12px; padding:12px; min-width:0;
}
.metric strong { display:block; font-size:20px; }
.metric small { color:var(--muted); }
.note {
  border:1px solid var(--line); border-radius:12px;
  padding:14px; font-size:13px; margin:15px 0 30px;
}
footer { text-align:center; border-top:1px solid var(--line); padding:22px; color:var(--muted); font-size:12px; }
@media(max-width:650px) {
  .grid { grid-template-columns:1fr; }
  header { align-items:flex-start; }
  .metrics { gap:6px; }
  .metric { padding:9px; }
  .metric strong { font-size:17px; }
}
</style>
</head>
<body>
<header>
  <div class="logo">TikTok <span>AI Studio</span></div>
  <div class="pill">LIVE ASSISTANT</div>
</header>

<main>
  <section class="hero">
    <div class="eyebrow">✦ YAYINCI KONTROL MERKEZİ</div>
    <h1>Canlı yayının için<br><span style="color:#d8b4fe">akıllı yardımcı.</span></h1>
    <p>Yorumları düzenle, cevap taslakları hazırla ve sesli asistan deneyimini planla. Gerçek yayın bağlantısı ayrıca kurulmalıdır.</p>
  </section>

  <section class="card" style="margin-bottom:18px">
    <h2>📡 Yayın bağlantısı</h2>
    <p id="connection" class="status">● Bağlantı kurulmadı — demo modu</p>
    <label for="username">TikTok kullanıcı adın (isteğe bağlı)</label>
    <input id="username" placeholder="@kullaniciadi" maxlength="50">
    <button class="action" onclick="showConnection()">Bağlantı durumunu kontrol et</button>
    <div id="connectionInfo" class="output hidden"></div>
  </section>

  <section class="grid">
    <article class="card">
      <h2>💬 Yorum asistanı</h2>
      <p>Bir yorum gir ve örnek cevap taslağı al.</p>
      <label for="comment">İzleyici yorumu</label>
      <textarea id="comment" maxlength="500" placeholder="Örn. Bu oyuna nasıl başladın?"></textarea>
      <button class="action" onclick="suggestReply()">Cevap taslağı hazırla</button>
      <div id="reply" class="output hidden" aria-live="polite"></div>
    </article>

    <article class="card">
      <h2>🎙️ Sesli asistan</h2>
      <p>Hazırlanan metni cihazının desteklediği sesle okut.</p>
      <label for="speechText">Okunacak metin</label>
      <textarea id="speechText" maxlength="1000" placeholder="Sesli okutmak istediğin metin"></textarea>
      <button class="action" onclick="speakText()">🔊 Sesli oku</button>
      <button class="action secondary" onclick="stopSpeech()">Sesi durdur</button>
      <p id="speechStatus" aria-live="polite"></p>
    </article>

    <article class="card">
      <h2>🧠 Yayın koçu</h2>
      <p>Yayında kullanabileceğin öneriler.</p>
      <label for="goal">Yayın hedefi</label>
      <select id="goal">
        <option value="sohbet">Sohbeti canlandırmak</option>
        <option value="soru">Soruları cevaplamak</option>
        <option value="oyun">Oyun yayını</option>
        <option value="tanisma">Yeni izleyicileri karşılamak</option>
      </select>
      <button class="action" onclick="coach()">Öneri göster</button>
      <div id="coachResult" class="output hidden" aria-live="polite"></div>
    </article>

    <article class="card">
      <h2>📊 Yayın özeti</h2>
      <p>Burada gerçek yayın verileri henüz bulunmuyor.</p>
      <div class="metrics">
        <div class="metric"><strong>—</strong><small>İzleyici</small></div>
        <div class="metric"><strong>—</strong><small>Yorum</small></div>
        <div class="metric"><strong>—</strong><small>Etkileşim</small></div>
      </div>
      <p style="font-size:12px">Gerçek sayılar ancak yetkili veri kaynağı bağlanınca gösterilir.</p>
    </article>
  </section>

  <div class="note">
    <strong>Demo bilgisi:</strong> Bu sayfadaki yorum cevapları ve yayın koçu yerel örneklerden oluşur; gerçek bir yapay zekâ servisine veya TikTok LIVE sohbetine bağlı değildir. Sesli okuma cihazın tarayıcı desteğine bağlıdır.
  </div>
</main>

<footer>© <span id="year"></span> TikTok AI Studio · Bağımsız prototip</footer>

<script>
document.getElementById("year").textContent = new Date().getFullYear();

function showConnection() {
  const name = document.getElementById("username").value.trim();
  const box = document.getElementById("connectionInfo");
  box.textContent = name
    ? name + " için bağlantı kurulmadı. Bu prototip TikTok hesabına erişmez."
    : "Henüz hesap bilgisi girilmedi. TikTok bağlantısı etkin değil.";
  box.classList.remove("hidden");
}

function suggestReply() {
  const comment = document.getElementById("comment").value.trim();
  if (!comment) {
    alert("Önce bir örnek yorum yaz.");
    return;
  }
  const box = document.getElementById("reply");
  box.textContent =
    "Örnek cevap taslağı:\n" +
    "“Güzel soru! 😊 " + comment.slice(0, 180) +
    " hakkında yayında biraz daha konuşalım.”\n\n" +
    "Not: Bu otomatik bir şablondur, yapay zekâ tarafından üretilmemiştir.";
  box.classList.remove("hidden");
  document.getElementById("speechText").value =
    "Güzel soru! Yayında biraz daha konuşalım.";
}

function speakText() {
  const text = document.getElementById("speechText").value.trim();
  const status = document.getElementById("speechStatus");
  if (!text) {
    status.textContent = "Önce okunacak bir metin gir.";
    return;
  }
  if (!("speechSynthesis" in window)) {
    status.textContent = "Bu tarayıcı sesli okumayı desteklemiyor.";
    return;
  }
  window.speechSynthesis.cancel();
  const utterance = new SpeechSynthesisUtterance(text);
  utterance.lang = "tr-TR";
  utterance.onstart = () => status.textContent = "Sesli okuma başladı.";
  utterance.onend = () => status.textContent = "Sesli okuma tamamlandı.";
  utterance.onerror = () => status.textContent = "Sesli okuma başlatılamadı.";
  window.speechSynthesis.speak(utterance);
}

function stopSpeech() {
  if ("speechSynthesis" in window) window.speechSynthesis.cancel();
  document.getElementById("speechStatus").textContent = "Ses durduruldu.";
}

function coach() {
  const tips = {
    sohbet: "İzleyicilere açık uçlu bir soru sor. Örn. Bugün hangi konuyu konuşalım?",
    soru: "Birden çok soru geldiyse benzer soruları grupla ve sırayla yanıtla.",
    oyun: "İzleyicilere bir sonraki tur için seçim yaptır veya oyun taktiğini anlat.",
    tanisma: "Yeni gelenleri selamla ve yayının konusunu kısa bir cümleyle açıkla."
  };
  const box = document.getElementById("coachResult");
  box.textContent = tips[document.getElementById("goal").value];
  box.classList.remove("hidden");
}
</script>
</body>
</html>
