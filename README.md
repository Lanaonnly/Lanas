
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5">
  <title>FRESH BREW · QR OTOMATIS</title>
  <!-- QR Code Generator -->
  <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', 'Poppins', system-ui, -apple-system, sans-serif;
      background: linear-gradient(145deg, #06372e 0%, #1e6f54 45%, #fff4db 100%);
      color: #02281e;
      line-height: 1.5;
    }

    /* HEADER DENGAN EFEK ES */
    header {
      text-align: center;
      padding: 40px 20px 35px;
      background: rgba(0, 0, 0, 0.2);
      backdrop-filter: blur(10px);
      border-bottom: 6px solid #ffd966;
      box-shadow: 0 12px 0 #154f3a;
      margin-bottom: 15px;
      position: relative;
    }

    header h1 {
      font-size: 3.8rem;
      color: #fffef0;
      text-shadow: 6px 6px 0 #1a5e45, 10px 10px 20px #00000050;
      letter-spacing: 3px;
    }

    header p {
      font-size: 1.8rem;
      background: #ffdb9cf5;
      color: #0c4433;
      display: inline-block;
      padding: 12px 45px;
      border-radius: 100px;
      font-weight: 800;
      backdrop-filter: blur(5px);
      border: 4px solid white;
      margin-top: 15px;
      box-shadow: 0 6px 0 #9b6e3c;
    }

    .container {
      max-width: 1350px;
      margin: 0 auto;
      padding: 15px 30px 50px;
    }

    /* JUDUL SECTION */
    .section-title {
      color: #fffde7;
      text-shadow: 4px 4px 0 #1b543e;
      font-size: 2.3rem;
      margin: 45px 0 30px 0;
      border-left: 20px solid #ffbc3b;
      padding-left: 25px;
      font-weight: 800;
      letter-spacing: 1px;
    }

    /* ===== GRID MENU ===== GAMBAR ES JELAS, VARIASI */
    .menu-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
      gap: 32px;
    }

    .menu-card {
      background: rgba(255, 255, 250, 0.94);
      backdrop-filter: blur(12px);
      border-radius: 40px 40px 30px 30px;
      overflow: hidden;
      box-shadow: 0 22px 30px -10px #001e16;
      transition: all 0.25s ease;
      border: 3px solid #fcf3c6;
      display: flex;
      flex-direction: column;
    }

    .menu-card:hover {
      transform: translateY(-10px) scale(1.01);
      box-shadow: 0 35px 35px -8px #02100c;
      background: white;
      border-color: #ffc164;
    }

    /* GAMBAR FULL HD, ES KELIHATAN SEGAR */
    .menu-card img {
      width: 100%;
      height: 230px;
      object-fit: cover;
      border-bottom: 8px solid #ffbc3b;
      transition: 0.2s;
      display: block;
    }

    .menu-card h3 {
      margin: 18px 20px 8px;
      font-size: 1.9rem;
      font-weight: 800;
      color: #134734;
      line-height: 1.2;
    }

    .price-tag {
      margin: 5px 20px;
      color: #0d784a;
      font-weight: 900;
      font-size: 1.7rem;
      display: flex;
      align-items: center;
      gap: 8px;
    }

    .btn-add {
      background: #1a6e4d;
      color: white;
      border: none;
      padding: 16px 22px;
      border-radius: 60px;
      margin: 12px 20px 22px;
      cursor: pointer;
      font-weight: 800;
      font-size: 1.2rem;
      box-shadow: 0 9px 0 #0a3d2c;
      transition: 0.07s;
      border: 2px solid #d4ffb0;
      letter-spacing: 1.5px;
    }

    .btn-add:hover {
      background: #279a6b;
      transform: translateY(-4px);
      box-shadow: 0 12px 0 #0a3d2c;
    }
    .btn-add:active {
      transform: translateY(5px);
      box-shadow: 0 5px 0 #0a3d2c;
    }

    /* ===== KERANJANG PREMIUM ===== */
    .cart-panel {
      background: #fffef5f2;
      backdrop-filter: blur(18px);
      padding: 38px 40px;
      border-radius: 80px 80px 50px 50px;
      margin-top: 70px;
      border: 5px solid #ffcf5c;
      box-shadow: 0 35px 35px #042118;
    }

    .cart-panel h2 {
      color: #1a4f3a;
      font-size: 2.3rem;
      border-left: 18px solid #f8b133;
      padding-left: 25px;
      margin-bottom: 30px;
      font-weight: 800;
    }

    #namaPemesan {
      padding: 18px 28px;
      width: 100%;
      border-radius: 120px;
      border: 4px solid #c9a55b;
      background: #fffae9;
      font-size: 1.3rem;
      margin-bottom: 25px;
      font-weight: 600;
      color: #1f4d32;
    }

    #cartList {
      background: #ead5aa;
      padding: 28px 35px;
      border-radius: 60px;
      list-style: none;
      box-shadow: inset 0 6px 14px #7a6242;
      font-size: 1.25rem;
      color: #15442e;
      font-weight: 600;
    }
    #cartList li {
      padding: 14px 0;
      border-bottom: 3px dashed #628574;
      font-size: 1.3rem;
    }

    #totalHarga {
      font-size: 2.6rem;
      font-weight: 900;
      color: #0e543a;
      background: #ffeaa7;
      padding: 20px 35px;
      border-radius: 70px;
      text-align: right;
      margin: 25px 0 20px;
      border: 4px solid #dc9f2b;
    }

    .btn-bayar-now {
      background: #b46d2e;
      font-size: 2rem;
      padding: 20px 35px;
      border-radius: 120px;
      font-weight: 900;
      box-shadow: 0 15px 0 #6a411f;
      border: 4px solid #ffeeb5;
      color: white;
      width: 100%;
      letter-spacing: 3px;
      transition: 0.08s;
    }
    .btn-bayar-now:hover {
      background: #dc8b45;
      transform: translateY(-6px);
      box-shadow: 0 20px 0 #6a411f;
    }

    /* ===== LOKASI ===== */
    .map-area {
      background: #205542d9;
      padding: 28px;
      border-radius: 70px;
      margin-top: 45px;
      backdrop-filter: blur(5px);
      border: 5px solid #ffc656;
    }
    iframe {
      border-radius: 50px;
      border: 6px solid #ffe087;
      height: 300px;
      width: 100%;
    }

    footer {
      text-align: center;
      color: #fffed8;
      padding: 40px;
      font-size: 1.5rem;
      font-weight: 700;
      background: #0a332bd9;
      backdrop-filter: blur(4px);
      margin-top: 70px;
      border-top: 8px solid #fec150;
    }

    /* ===== POPUP METODE (bersih & elegan) ===== */
    .popup-method {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(3, 44, 30, 0.9);
      backdrop-filter: blur(9px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 999;
    }
    .method-container {
      background: #fffef3;
      padding: 40px 35px;
      border-radius: 90px 30px 90px 30px;
      border: 10px solid #fed058;
      max-width: 750px;
      width: 90%;
      text-align: center;
    }
    .method-container h2 {
      color: #1b5a40;
      font-size: 2.6rem;
      margin-bottom: 30px;
      text-shadow: 3px 3px 0 #ffeeb5;
      border: none;
    }
    .method-flex {
      display: flex;
      flex-wrap: wrap;
      justify-content: center;
      gap: 20px;
      margin-bottom: 25px;
    }
    .btn-metode {
      background: #226f53;
      box-shadow: 0 9px 0 #0d3f2e;
      border: 3px solid #ffd78a;
      color: white;
      padding: 18px 28px;
      border-radius: 70px;
      font-size: 1.5rem;
      font-weight: 800;
      display: flex;
      align-items: center;
      gap: 10px;
      transition: 0.07s;
    }
    .btn-metode:hover {
      background: #379e78;
      transform: translateY(-5px);
      box-shadow: 0 14px 0 #0d3f2e;
    }

    /* ===== POPUP QR OTOMATIS (TANPA TOMBOL KONFIRMASI) ===== */
    .popup-qr-auto {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(2, 36, 26, 0.92);
      backdrop-filter: blur(10px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }
    .qr-panel {
      background: linear-gradient(150deg, #ffffff, #fffbe3);
      padding: 40px 35px;
      border-radius: 90px 30px 90px 30px;
      border: 12px solid #ffb82e;
      max-width: 520px;
      width: 90%;
      text-align: center;
      box-shadow: 0 40px 50px #021610;
    }
    .qr-panel h3 {
      font-size: 2.8rem;
      color: #1a5e45;
      text-shadow: 4px 4px 0 #ffe69b;
      margin-bottom: 10px;
    }
    .nomor-besar {
      background: #19523d;
      color: white;
      font-size: 1.9rem;
      font-weight: 900;
      padding: 14px 15px;
      border-radius: 120px;
      letter-spacing: 4px;
      margin: 15px 0 20px;
      border: 4px solid #ffd966;
      word-break: break-word;
    }
    #qrcode {
      display: flex;
      justify-content: center;
      margin: 15px 0 15px;
    }
    #qrcode img {
      padding: 14px;
      background: white;
      border-radius: 40px;
      border: 8px solid #1f734e;
      width: 220px;
      height: 220px;
    }
    .qr-hint {
      font-size: 1.3rem;
      background: #e7dc9a;
      padding: 14px;
      border-radius: 70px;
      color: #0a3a2c;
      font-weight: 700;
      margin-top: 15px;
    }
    .btn-kembali-qr {
      background: #7c6242;
      box-shadow: 0 9px 0 #4f3d2a;
      border: 3px solid #fad68b;
      color: white;
      padding: 16px 30px;
      border-radius: 70px;
      font-size: 1.4rem;
      font-weight: 800;
      margin-top: 25px;
    }

    /* tidak ada tombol "saya sudah bayar" — HAPUS total */
    /* QR langsung kirim WA ke toko */

    .clear-both { clear: both; }
    .no-wa-badge {
      background: #ffdc9f;
      color: #043d2b;
      padding: 8px 30px;
      border-radius: 60px;
      font-weight: 800;
      display: inline-block;
    }
  </style>
</head>
<body>

<header>
  <h1>🧊 FRESH BREW</h1>
  <p>🍧 ES SEGAR · GAMBAR HD</p>
</header>

<div class="container">

  <!-- ========== MENU DENGAN 13+ VARIASI GAMBAR ES ========= -->
  <div class="section-title">🥤 MINUMAN FAVORIT — VISUAL JERNIH</div>
  <div class="menu-grid" id="menuList"></div>

  <!-- ========== KERANJANG ========= -->
  <div class="cart-panel">
    <h2>🛒 PESANAN KAMU</h2>
    <input type="text" id="namaPemesan" placeholder="✏️ Nama lengkap (contoh: Sheila)" autocomplete="off">
    <ul id="cartList"></ul>
    <div id="totalHarga">💰 Total: Rp 0</div>
    <button class="btn-bayar-now" onclick="tampilkanPilihanMetode()">💳 BAYAR · QR OTOMATIS</button>
  </div>

  <!-- ========== LOKASI TOKO ========= -->
  <div class="section-title">📍 LOKASI KAMI</div>
  <div class="map-area">
    <p style="color:white; font-size:1.8rem; margin-bottom:18px; font-weight:800;">⛽ Jl. Ir Soetami (Depan Pom Bensin)</p>
    <iframe 
      src="https://maps.google.com/maps?q=Jl.%20Ir.%20Soetami&t=&z=15&ie=UTF8&iwloc=&output=embed"
      allowfullscreen loading="lazy">
    </iframe>
  </div>
</div>

<!-- POPUP 1: PILIH METODE PEMBAYARAN (CASH / E-WALLET) -->
<div class="popup-method" id="popupMethod">
  <div class="method-container">
    <h2>🧾 PILIH METODE</h2>
    <div class="method-flex">
      <button class="btn-metode" onclick="prosesMetode('Cash')">💵 Cash</button>
      <button class="btn-metode" onclick="prosesMetode('Dana')">💙 Dana</button>
      <button class="btn-metode" onclick="prosesMetode('OVO')">💜 OVO</button>
      <button class="btn-metode" onclick="prosesMetode('GoPay')">💚 GoPay</button>
      <button class="btn-metode" onclick="prosesMetode('ShopeePay')">🛒 ShopeePay</button>
    </div>
    <button onclick="tutupPopupMethod()" style="background:#6e4f3a; box-shadow:0 9px 0 #493626; padding:16px 40px; border-radius:70px; color:white; font-size:1.4rem; border:3px solid #f5cf86; margin-top:10px;">✖ Tutup</button>
  </div>
</div>

<!-- POPUP 2: QR OTOMATIS (UNTUK DANA, OVO, GOPAY, SHOPEEPAY) -->
<!-- TIDAK ADA TOMBOL "SUDAH BAYAR" — WA OTOMATIS TERKIRIM SAAT QR MUNCUL -->
<div class="popup-qr-auto" id="popupQR">
  <div class="qr-panel">
    <h3 id="qrTitle">💙 Dana</h3>
    <div id="qrcode"></div>
    <div class="nomor-besar" id="qrNomor">0838 7216 1233</div>
    <div class="qr-hint">
      ⚡ SCAN QR · OTOMATIS TERKIRIM WA KE TOKO<br>
      <span style="background:#1a543c; color:#ffde8a; padding:7px 20px; border-radius:80px; display:inline-block; margin-top:10px;">🏢 0838-7216-1233 (PT)</span>
    </div>
    <button class="btn-kembali-qr" onclick="tutupQR()">◀ Kembali</button>
  </div>
</div>

<footer>
  🧊 FRESH BREW DRINK — SINCE 2026  <span class="no-wa-badge">📞 0838 7216 1233 (e-wallet/WA)</span>
</footer>

<script>
  // ========== MENU DENGAN GAMBAR ESPRESSO/ES YANG JELAS, VARIASI BERBEDA ==========
  const menu = [
    { nama: "Es Teh Manis", harga: 5000, gambar: "https://images.unsplash.com/photo-1556679343-c1c1c1d56c6d?w=700&auto=format&fit=crop&q=80" },
    { nama: "Es Teh Lemon", harga: 8000, gambar: "https://images.unsplash.com/photo-1558640479-8242c0c8b9b9?w=700&auto=format&fit=crop&q=80" },
    { nama: "Thai Tea", harga: 12000, gambar: "https://images.unsplash.com/photo-1604908176997-125f25cc6f3d?w=700&auto=format&fit=crop&q=80" },
    { nama: "Matcha Latte", harga: 15000, gambar: "https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=700&auto=format&fit=crop&q=80" },
    { nama: "Es Kopi Susu", harga: 13000, gambar: "https://images.unsplash.com/photo-1509042239860-f550ce710b93?w=700&auto=format&fit=crop&q=80" },
    { nama: "Cappuccino", harga: 15000, gambar: "https://images.unsplash.com/photo-1511920170033-f8396924c348?w=700&auto=format&fit=crop&q=80" },
    { nama: "Americano", harga: 12000, gambar: "https://images.unsplash.com/photo-1498804103079-a6351b050096?w=700&auto=format&fit=crop&q=80" },
    { nama: "Kopi Gula Aren", harga: 14000, gambar: "https://images.unsplash.com/photo-1495474472287-4d71bcdd2085?w=700&auto=format&fit=crop&q=80" },
    { nama: "Chocolate Ice", harga: 15000, gambar: "https://images.unsplash.com/photo-1572490122747-3968b75cc699?w=700&auto=format&fit=crop&q=80" },
    { nama: "Lychee Tea", harga: 13000, gambar: "https://images.unsplash.com/photo-1556679343-c1c1c1d56c6d?w=700&bri=1.1&con=-5&sat=10&q=80" },
    { nama: "Mango Smoothie", harga: 18000, gambar: "https://images.unsplash.com/photo-1558640479-8242c0c8b9b9?w=700&bri=1.2&con=5&q=80" },
    { nama: "Red Velvet", harga: 16000, gambar: "https://images.unsplash.com/photo-1572442388796-11668a67e53d?w=700&sat=15&q=80" },
    { nama: "Taro Latte", harga: 15000, gambar: "https://images.unsplash.com/photo-1604908176997-125f25cc6f3d?w=700&bri=0.95&con=8&q=80" },
    { nama: "Vanilla Shake", harga: 17000, gambar: "https://images.unsplash.com/photo-1572490122747-3968b75cc699?w=700&bri=1.1&q=80" }
  ];

  // ========== CART & VARIABEL ==========
  let cart = [];
  const WA_TOKO = "6283872161233";  // NOMOR PT / TOKO (TIDAK KE PEMESAN)
  let selectedMethod = "";

  // ========== RENDER MENU ==========
  function renderMenu() {
    let html = "";
    menu.forEach((item, idx) => {
      html += `<div class="menu-card">
        <img src="${item.gambar}" alt="${item.nama}" loading="lazy">
        <h3>${item.nama}</h3>
        <p class="price-tag">💵 Rp ${item.harga.toLocaleString()}</p>
        <button class="btn-add" onclick="tambahKeCart(${idx})">➕ TAMBAH</button>
      </div>`;
    });
    document.getElementById("menuList").innerHTML = html;
  }

  window.tambahKeCart = function(index) {
    cart.push(menu[index]);
    updateCart();
  };

  function updateCart() {
    let listHtml = "";
    let total = 0;
    cart.forEach(item => {
      listHtml += `<li>🧊 ${item.nama} — Rp ${item.harga.toLocaleString()}</li>`;
      total += item.harga;
    });
    document.getElementById("cartList").innerHTML = listHtml;
    document.getElementById("totalHarga").innerHTML = `💰 Total: Rp ${total.toLocaleString()}`;
  }

  // ========== POPUP METODE ==========
  window.tampilkanPilihanMetode = function() {
    const nama = document.getElementById("namaPemesan").value.trim();
    if (nama === "") {
      alert("✋ Isi nama pemesan dulu ya!");
      return;
    }
    if (cart.length === 0) {
      alert("🛒 Keranjang masih kosong, pilih minuman!");
      return;
    }
    document.getElementById("popupMethod").style.display = "flex";
  };

  window.tutupPopupMethod = function() {
    document.getElementById("popupMethod").style.display = "none";
  };

  // ========== PROSES METODE ==========
  window.prosesMetode = function(metode) {
    selectedMethod = metode;
    tutupPopupMethod();  // tutup popup pilihan

    if (metode === "Cash") {
      // CASH → LANGSUNG WA KE TOKO, TANPA QR
      kirimWaKeToko(metode);
    } else {
      // E-WALLET → TAMPILKAN QR + OTOMATIS KIRIM WA KE TOKO (TANPA TOMBOL KONFIRMASI)
      tampilkanQRdanKirimWA(metode);
    }
  };

  // ========== TAMPILKAN QR + KIRIM WA OTOMATIS (HANYA KE TOKO) ==========
  function tampilkanQRdanKirimWA(metode) {
    // bersihkan QR sebelumnya
    document.getElementById("qrcode").innerHTML = "";
    
    // nomor tujuan display
    const nomorDisplay = "0838 7216 1233";
    const nomorMurni = "083872161233";
    
    // set judul metode
    let titleIcon = "";
    if (metode === "Dana") titleIcon = "💙 Dana";
    else if (metode === "OVO") titleIcon = "💜 OVO";
    else if (metode === "GoPay") titleIcon = "💚 GoPay";
    else if (metode === "ShopeePay") titleIcon = "🛒 ShopeePay";
    else titleIcon = metode;
    document.getElementById("qrTitle").innerText = titleIcon;
    document.getElementById("qrNomor").innerText = nomorDisplay;

    // isi QR string
    let qrString = `${metode}: 083872161233 (Fresh Brew)`;
    if (metode === "Dana") qrString = "DANA: 083872161233 an. FRESH BREW";
    else if (metode === "OVO") qrString = "OVO: 083872161233 (BREW)";
    else if (metode === "GoPay") qrString = "GOPAY: 083872161233 - brew";
    else if (metode === "ShopeePay") qrString = "SHOPEEPAY: 083872161233 (minuman)";

    new QRCode(document.getElementById("qrcode"), {
      text: qrString,
      width: 230,
      height: 230,
      colorDark: "#0e523a",
      colorLight: "#fffef0",
      correctLevel: QRCode.CorrectLevel.H
    });

    // TAMPILKAN POPUP QR
    document.getElementById("popupQR").style.display = "flex";

    // OTOMATIS KIRIM WA KE TOKO (PT) — TANPA TOMBOL "SAYA SUDAH BAYAR"
    kirimWaKeToko(metode);
  }

  // ========== KIRIM WA HANYA KE TOKO (PT) ==========
  function kirimWaKeToko(metodeBayar) {
    const nama = document.getElementById("namaPemesan").value.trim() || "Pemesan";
    let detailPesanan = "";
    let totalHarga = 0;

    cart.forEach(c => {
      detailPesanan += `• ${c.nama} - Rp ${c.harga.toLocaleString()}%0A`;
      totalHarga += c.harga;
    });

    const totalStr = `Rp ${totalHarga.toLocaleString()}`;
    
    // PESAN UNTUK TOKO (PT) — BUKAN UNTUK PEMESAN
    let pesan = `🧊 *FRESH BREW · PESANAN MASUK*%0A%0A`;
    pesan += `👤 *Nama:* ${nama}%0A`;
    pesan += `📋 *Pesanan:*%0A${detailPesanan}%0A`;
    pesan += `💵 *Total: ${totalStr}*%0A`;
    pesan += `💳 *Metode Bayar:* ${metodeBayar}%0A`;

    if (metodeBayar !== "Cash") {
      pesan += `✅ *QR DITAMPILKAN* — bayar ke 083872161233 (${metodeBayar})%0A`;
      pesan += `⏱️ Pelanggan telah scan QR dan melakukan pembayaran.%0A`;
    } else {
      pesan += `💰 *CASH* — bayar di kasir langsung.%0A`;
    }

    pesan += `📍 *Lokasi:* Jl. Ir Soetami (Depan Pom Bensin)%0A`;
    pesan += `✨ Segera siapkan pesanan. Terima kasih!`;

    // BUKA WA DENGAN NOMOR TOKO (PT)
    window.open(`https://wa.me/${WA_TOKO}?text=${pesan}`, '_blank');
  }

  // ========== TUTUP POPUP QR ==========
  window.tutupQR = function() {
    document.getElementById("popupQR").style.display = "none";
    document.getElementById("qrcode").innerHTML = ""; // hapus qr
  };

  // ========== CLICK OUTSIDE ==========
  window.onclick = function(e) {
    const popMethod = document.getElementById("popupMethod");
    const popQR = document.getElementById("popupQR");
    if (e.target === popMethod) popMethod.style.display = "none";
    if (e.target === popQR) {
      popQR.style.display = "none";
      document.getElementById("qrcode").innerHTML = "";
    }
  };

  // ========== INIT ==========
  renderMenu();
  updateCart(); // keranjang kosong
</script>

<!-- QR FALLBACK -->
<script>
  if (typeof QRCode === "undefined") {
    console.warn("QR library tidak dimuat, refresh mungkin diperlukan");
  }
</script>

</body>
</html>
