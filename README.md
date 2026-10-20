
<!DOCTYPE html>
<html lang="tr">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <meta name="theme-color" content="#111827">
  <meta name="description" content="Ücretsiz PDF, metin, görsel ve hesaplama araçları.">
  <title>Pratik Araçlar | Ücretsiz Online Araçlar</title>

  <style>
    * {
      box-sizing: border-box;
      margin: 0;
      padding: 0;
    }

    :root {
      --bg: #0b1020;
      --panel: #151d30;
      --text: #f5f7ff;
      --muted: #a7b0c5;
      --accent: #7c6cff;
      --border: #28334b;
    }

    body {
      font-family: Arial, sans-serif;
      background: var(--bg);
      color: var(--text);
      line-height: 1.6;
    }

    a {
      color: inherit;
      text-decoration: none;
    }

    .container {
      width: min(1100px, 92%);
      margin: auto;
    }

    header {
      border-bottom: 1px solid var(--border);
      background: #0b1020;
      position: sticky;
      top: 0;
      z-index: 10;
    }

    .nav {
      min-height: 70px;
      display: flex;
      align-items: center;
      justify-content: space-between;
      gap: 15px;
    }

    .logo {
      font-size: 21px;
      font-weight: 800;
    }

    .logo span {
      color: #a99cff;
    }

    nav {
      display: flex;
      gap: 18px;
      flex-wrap: wrap;
      font-size: 14px;
      color: var(--muted);
    }

    nav a:hover {
      color: white;
    }

    .hero {
      text-align: center;
      padding: 70px 0 42px;
    }

    .tag {
      display: inline-block;
      background: #211e45;
      color: #c8c0ff;
      padding: 7px 13px;
      border-radius: 30px;
      font-size: 13px;
      margin-bottom: 18px;
    }

    h1 {
      font-size: clamp(32px, 6vw, 52px);
      line-height: 1.15;
      margin-bottom: 18px;
    }

    h1 span {
      color: #a99cff;
    }

    .hero p {
      color: var(--muted);
      max-width: 590px;
      margin: 0 auto 25px;
    }

    .search {
      display: block;
      width: min(560px, 100%);
      margin: auto;
      padding: 16px 18px;
      border: 1px solid var(--border);
      border-radius: 14px;
      background: var(--panel);
      color: white;
      font-size: 16px;
      outline: none;
    }

    .search:focus {
      border-color: var(--accent);
    }

    .section {
      padding: 28px 0 42px;
    }

    .section-title {
      font-size: 25px;
      margin-bottom: 7px;
    }

    .section-desc {
      color: var(--muted);
      margin-bottom: 22px;
    }

    .grid {
      display: grid;
      grid-template-columns: repeat(3, minmax(0, 1fr));
      gap: 16px;
    }

    .card {
      display: block;
      padding: 22px;
      background: var(--panel);
      border: 1px solid var(--border);
      border-radius: 17px;
      transition: .2s;
    }

    .card:hover {
      transform: translateY(-3px);
      border-color: var(--accent);
    }

    .emoji {
      font-size: 30px;
      margin-bottom: 12px;
    }

    .card h3 {
      font-size: 18px;
      margin-bottom: 8px;
    }

    .card p {
      color: var(--muted);
      font-size: 14px;
    }

    .status {
      display: inline-block;
      font-size: 12px;
      color: #c8c0ff;
      background: #252148;
      border-radius: 20px;
      padding: 4px 9px;
      margin-top: 14px;
    }

    .about {
      background: #11182a;
      border: 1px solid var(--border);
      border-radius: 18px;
      padding: 26px;
      margin: 10px 0 45px;
    }

    .about p {
      color: var(--muted);
      margin-top: 8px;
    }

    footer {
      border-top: 1px solid var(--border);
      padding: 25px 0;
      color: var(--muted);
      font-size: 13px;
      text-align: center;
    }

    .hidden {
      display: none !important;
    }

    @media (max-width: 750px) {
      .grid {
        grid-template-columns: repeat(2, minmax(0, 1fr));
      }

      .nav {
        align-items: flex-start;
        flex-direction: column;
        padding: 15px 0;
      }

      nav {
        gap: 13px;
      }

      .hero {
        padding-top: 48px;
      }
    }

    @media (max-width: 460px) {
      .grid {
        grid-template-columns: 1fr;
      }

      .card {
        padding: 19px;
      }
    }
  </style>
</head>

<body>
  <header>
    <div class="container nav">
      <a class="logo" href="#">Pratik <span>Araçlar</span></a>
      <nav>
        <a href="#araclar">Araçlar</a>
        <a href="#pdf">PDF</a>
        <a href="#metin">Metin</a>
        <a href="#hakkinda">Hakkında</a>
      </nav>
    </div>
  </header>

  <main class="container">
    <section class="hero">
      <div class="tag">Ücretsiz çevrim içi araçlar</div>
      <h1>İşlerini kolaylaştır,<br><span>zaman kazan.</span></h1>
      <p>
        PDF, metin, görsel ve hesaplama işlemlerini
        tek bir yerde keşfet. Ücretsiz araçlarını bul.
      </p>
      <input
        id="search"
        class="search"
        type="search"
        placeholder="Araç ara... Örn: PDF, hesap makinesi"
        aria-label="Araç ara"
      >
    </section>

    <section class="section" id="araclar">
      <h2 class="section-title">Araç koleksiyonu</h2>
      <p class="section-desc">İhtiyacın olan aracı seç.</p>

      <div class="grid" id="toolGrid">
        <a class="card" id="pdf" href="#pdf" data-search="pdf birleştir birleştirme">
          <div class="emoji">📄</div>
          <h3>PDF Birleştirici</h3>
          <p>Birden fazla PDF dosyasını tek dosyada birleştirmek için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="pdf ayır böl sayfa">
          <div class="emoji">✂️</div>
          <h3>PDF Sayfalarını Ayır</h3>
          <p>PDF dosyandaki sayfaları ayrı dosyalara ayırmak için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="pdf görsel resim jpg png dönüştür">
          <div class="emoji">🖼️</div>
          <h3>PDF'den Görsele</h3>
          <p>PDF sayfalarını görsel biçimine dönüştürmek için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="pdf sıkıştır küçült boyut">
          <div class="emoji">📦</div>
          <h3>PDF Sıkıştırıcı</h3>
          <p>PDF dosyalarının boyutunu azaltmak için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" id="metin" href="#araclar" data-search="metin kelime karakter sayacı">
          <div class="emoji">📝</div>
          <h3>Metin Sayacı</h3>
          <p>Metindeki kelime ve karakter sayısını hesaplamak için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="büyük küçük harf metin dönüştür">
          <div class="emoji">🔠</div>
          <h3>Harf Dönüştürücü</h3>
          <p>Metinleri büyük veya küçük harfe dönüştürmek için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="hesap makinesi matematik hesaplama">
          <div class="emoji">🧮</div>
          <h3>Hesap Makinesi</h3>
          <p>Günlük matematik işlemlerini kolayca yapmak için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="yüzde hesaplama indirim">
          <div class="emoji">📊</div>
          <h3>Yüzde Hesaplama</h3>
          <p>Yüzde, indirim ve oran hesaplamaları için.</p>
          <span class="status">Yakında</span>
        </a>

        <a class="card" href="#araclar" data-search="resim görsel boyut küçültme">
          <div class="emoji">🎨</div>
          <h3>Görsel Araçları</h3>
          <p>Görseller için pratik dönüştürme araçları.</p>
          <span class="status">Yakında</span>
        </a>
      </div>

      <p id="noResults" class="section-desc hidden" style="margin-top:20px">
        Aradığın araç bulunamadı.
      </p>
    </section>

    <section class="about" id="hakkinda">
      <h2>Pratik Araçlar hakkında</h2>
      <p>
        Amacımız günlük dijital işlerini kolaylaştıran,
        kullanımı basit ve ücretsiz araçları tek yerde sunmak.
        Yeni araçlar zamanla eklenecek.
      </p>
    </section>
  </main>

  <footer>
    <div class="container">
      © <span id="year"></span> Pratik Araçlar · Kolay, hızlı ve pratik.
    </div>
  </footer>

  <script>
    const search = document.getElementById("search");
    const cards = document.querySelectorAll(".card");
    const noResults = document.getElementById("noResults");

    document.getElementById("year").textContent =
      new Date().getFullYear();

    search.addEventListener("input", function () {
      const query = this.value.trim().toLocaleLowerCase("tr-TR");
      let visible = 0;

      cards.forEach(function (card) {
        const text = (
          card.innerText + " " + card.dataset.search
        ).toLocaleLowerCase("tr-TR");

        const match = text.includes(query);
        card.classList.toggle("hidden", !match);

        if (match) visible++;
      });

      noResults.classList.toggle("hidden", visible !== 0);
    });
  </script>
</body>
</html>
