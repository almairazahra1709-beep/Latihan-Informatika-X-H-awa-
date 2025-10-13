<!DOCTYPE html>
<html lang="id">
<head>
  <meta charset="UTF-8">
  <title>Mind Map: Yura Yunita</title>
  <style>
    body {
      font-family: 'Segoe UI', sans-serif;
      background: #f7f7f7;
      padding: 20px;
      max-width: 700px;
      margin: auto;
    }

    h1 {
      text-align: center;
      color: #cc3366;
    }

    .accordion {
      background-color: #ffffff;
      color: #333;
      cursor: pointer;
      padding: 15px;
      width: 100%;
      border: none;
      outline: none;
      text-align: left;
      font-size: 16px;
      transition: 0.4s;
      margin-bottom: 5px;
      border-radius: 5px;
      box-shadow: 0 2px 5px rgba(0,0,0,0.1);
    }

    .accordion.active, .accordion:hover {
      background-color: #ffe6f0;
    }

    .panel {
      padding: 0 15px;
      background-color: white;
      display: none;
      overflow: hidden;
      border-left: 4px solid #cc3366;
      border-radius: 0 0 5px 5px;
    }
  </style>
</head>
<body>

  <h1>Mind Map: Yura Yunita</h1>

  <button class="accordion">1. Identitas Pribadi</button>
  <div class="panel">
    <p>Nama asli: Yunita Rachman<br>
    Nama panggung: Yura Yunita<br>
    Lahir: Bandung, 9 Juni 1991<br>
    Agama: Islam</p>
  </div>

  <button class="accordion">2. Pendidikan</button>
  <div class="panel">
    <p>Lulusan Ilmu Komunikasi, UNPAD - Jurusan Humas</p>
  </div>

  <button class="accordion">3. Awal Karier</button>
  <div class="panel">
    <p>Ikut The Voice Indonesia (2013).<br>
    Debut: Album "Yura" (2014).<br>
    Kolaborasi awal: Glenn Fredly - "Cinta dan Rahasia".</p>
  </div>

  <button class="accordion">4. Gaya Musik & Tema</button>
  <div class="panel">
    <p>Genre: Pop, Soul, Jazz.<br>
    Tema: Self-love, pengalaman pribadi, kesehatan mental.</p>
  </div>

  <button class="accordion">5. Karya Terkenal</button>
  <div class="panel">
    <ul>
      <li>Album: Yura (2014), Merakit (2018), Tutur Batin (2021)</li>
      <li>Lagu: "Berawal Dari Tatap", "Cinta dan Rahasia", "Tutur Batin"</li>
    </ul>
  </div>

  <button class="accordion">6. Prestasi</button>
  <div class="panel">
    <p>AMI Awards, Indonesian Choice Awards, dan banyak lagi.</p>
  </div>

  <button class="accordion">7. Kehidupan Pribadi</button>
  <div class="panel">
    <p>Menikah dengan Donne Maula. Aktif di proyek sosial & musik independen.</p>
  </div>

  <script>
    const acc = document.querySelectorAll(".accordion");
    acc.forEach(button => {
      button.addEventListener("click", function () {
        this.classList.toggle("active");
        const panel = this.nextElementSibling;
        if (panel.style.display === "block") {
          panel.style.display = "none";
        } else {
          panel.style.display = "block";
        }
      });
    });
  </script>

</body>
</html>
