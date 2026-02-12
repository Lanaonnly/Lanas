
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.5">
  <title>FRESH BREW · QR SEMPURNA</title>
  <!-- QR Code Generator -->
  <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', 'Poppins', system-ui, sans-serif;
      background: linear-gradient(145deg, #07382e 0%, #1f6e54 45%, #fff7e0 100%);
      color: #02281e;
      line-height: 1.5;
    }

    /* HEADER BERSIH - TIDAK ADA QR INSTAN */
    header {
      text-align: center;
      padding: 35px 20px;
      background: rgba(0, 0, 0, 0.2);
      backdrop-filter: blur(8px);
      border-bottom: 6px solid #ffd966;
      box-shadow: 0 12px 0 #154f3a;
      margin-bottom: 10px;
    }

    header h1 {
      font-size: 3.8rem;
      color: #fffef0;
      text-shadow: 6px 6px 0 #1a5e45;
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
      border: 4px solid white;
      margin-top: 15px;
    }

    .container {
      max-width: 1350px;
      margin: 0 auto;
      padding: 15px 30px 50px;
    }

    .section-title {
      color: #fffde7;
      text-shadow: 4px 4px 0 #1b543e;
      font-size: 2.3rem;
      margin: 45px 0 30px 0;
      border-left: 20px solid #ffbc3b;
      padding-left: 25px;
      font-weight: 800;
    }

    /* ===== MENU GRID ===== */
    .menu-grid {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(270px, 1fr));
      gap: 32px;
    }

    .menu-card {
      background: rgba(255, 255, 250, 0.94);
      backdrop-filter: blur(12px);
      border-radius: 40px;
      overflow: hidden;
      box-shadow: 0 22px 30px -10px #001e16;
      transition: 0.25s;
      border: 3px solid #fcf3c6;
    }

    .menu-card:hover {
      transform: translateY(-8px);
      background: white;
      border-color: #ffc164;
    }

    .menu-card img {
      width: 100%;
      height: 230px;
      object-fit: cover;
      border-bottom: 8px solid #ffbc3b;
      display: block;
    }

    .menu-card h3 {
      margin: 18px 20px 8px;
      font-size: 1.9rem;
      font-weight: 800;
      color: #134734;
    }

    .price-tag {
      margin: 5px 20px;
      color: #0d784a;
      font-weight: 900;
      font-size: 1.7rem;
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
      width: calc(100% - 40px);
    }

    .btn-add:hover {
      background: #279a6b;
      transform: translateY(-4px);
      box-shadow: 0 12px 0 #0a3d2c;
    }

    /* ===== KERANJANG ===== */
    .cart-panel {
      background: #fffef5f2;
      backdrop-filter: blur(18px);
      padding: 38px 40px;
      border-radius: 80px;
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
    }

    #cartList {
      background: #ead5aa;
      padding: 28px 35px;
      border-radius: 60px;
      list-style: none;
      box-shadow: inset 0 6px 14px #7a6242;
      font-size: 1.3rem;
      color: #15442e;
      font-weight: 600;
    }
    
    #cartList li {
      padding: 14px 0;
      border-bottom: 3px dashed #628574;
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

    .btn-bayar {
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
      cursor: pointer;
      transition: 0.08s;
    }
    
    .btn-bayar:hover {
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
      margin-top: 70px;
      border-top: 8px solid #fec150;
    }

    /* ===== POPUP METODE ===== */
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
      border-radius: 90px;
      border: 10px solid #fed058;
      max-width: 750px;
      width: 90%;
      text-align: center;
    }
    
    .method-container h2 {
      color: #1b5a40;
      font-size: 2.6rem;
      margin-bottom: 30px;
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
      cursor: pointer;
      transition: 0.07s;
      border: none;
      border-bottom: 4px solid #ffd78a;
    }
    
    .btn-metode:hover {
      background: #379e78;
      transform: translateY(-5px);
      box-shadow: 0 14px 0 #0d3f2e;
    }

    /* ===== POPUP QR - MURNI HANYA QR + NOMOR ===== */
    .popup-qr {
      position: fixed;
      top: 0; left: 0; width: 100%; height: 100%;
      background: rgba(2, 36, 26, 0.95);
      backdrop-filter: blur(10px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }
    
    .qr-panel {
      background: white;
      padding: 40px 35px;
      border-radius: 60px;
      border: 12px solid #ffb82e;
      max-width: 500px;
      width: 90%;
      text-align: center;
      box-shadow: 0 40px 50px #021610;
    }
    
    .qr-panel h3 {
      font-size: 2.5rem;
      color: #1a5e45;
      margin-bottom: 15px;
      font-weight: 900;
    }
    
    .nomor-qr {
      background: #19523d;
      color: white;
      font-size: 1.9rem;
      font-weight: 900;
      padding: 14px 15px;
      border-radius: 120px;
      letter-spacing: 4px;
      margin: 15px 0 25px;
      border: 4px solid #ffd966;
    }
    
    #qrcode {
      display: flex;
      justify-content: center;
      margin: 10px 0 20px;
    }
    
    #qrcode img {
      padding: 15px;
      background: white;
      border-radius: 30px;
      border: 6px solid #1f734e;
      width: 230px;
      height: 230px;
    }
    
    .btn-kembali {
      background: #7c6242;
      box-shadow: 0 9px 0 #4f3d2a;
      color: white;
      padding: 16px 35px;
      border-radius: 70px;
      font-size: 1.4rem;
      font-weight: 800;
      margin-top: 25px;
      border: none;
      border-bottom: 4px solid #fad68b;
      cursor: pointer;
    }
    
    .btn-kembali:hover {
      background: #9c7a54;
      transform: translateY(-3px);
      box-shadow: 0 12px 0 #4f3d2a;
    }

    /* TIDAK ADA TEKS BERLEBIHAN */
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
  <p>🍹 ES SEGAR · GAMBAR HD</p>
</header>

<div class="container">

  <!-- ========== MENU ========= -->
  <div class="section-title">🥤 MINUMAN FAVORIT</div>
  <div class="menu-grid" id="menuList"></div>

  <!-- ========== KERANJANG ========= -->
  <div class="cart-panel">
    <h2>🛒 PESANAN ANDA</h2>
    <input type="text" id="namaPemesan" placeholder="✏️ Masukkan nama pemesan" autocomplete="off">
    <ul id="cartList"></ul>
    <div id="totalHarga">💰 Total: Rp 0</div>
    <button class="btn-bayar" onclick="bukaPopupMetode()">💳 BAYAR SEKARANG</button>
  </div>

  <!-- ========== LOKASI ========= -->
  <div class="section-title">📍 LOKASI</div>
  <div class="map-area">
    <p style="color:white; font-size:1.8rem; margin-bottom:18px; font-weight:800;">⛽ Jl. Ir Soetami (Depan Pom Bensin)</p>
    <iframe 
      src="https://maps.google.com/maps?q=Jl.%20Ir.%20Soetami&t=&z=15&ie=UTF8&iwloc=&output=embed"
      allowfullscreen loading="lazy">
    </iframe>
  </div>
</div>

<!-- POPUP 1: PILIH METODE (CASH / E-WALLET) -->
<div class="popup-method" id="popupMetode">
  <div class="method-container">
    <h2>🧾 PILIH METODE</h2>
    <div class="method-flex">
      <button class="btn-metode" onclick="prosesMetode('Cash')">💵 Cash</button>
      <button class="btn-metode" onclick="prosesMetode('Dana')">💙 Dana</button>
      <button class="btn-metode" onclick="prosesMetode('OVO')">💜 OVO</button>
      <button class="btn-metode" onclick="prosesMetode('GoPay')">💚 GoPay</button>
      <button class="btn-metode" onclick="prosesMetode('ShopeePay')">🛒 ShopeePay</button>
    </div>
    <button onclick="tutupPopupMetode()" style="background:#6e4f3a; box-shadow:0 9px 0 #493626; padding:16px 40px; border-radius:70px; color:white; font-size:1.4rem; border:none; border-bottom:4px solid #f5cf86; margin-top:10px; cursor:pointer;">✖ Tutup</button>
  </div>
</div>

<!-- POPUP 2: QR CODE - MURNI HANYA QR + NOMOR, TIDAK ADA TEKS LAIN -->
<!-- TIDAK ADA TOMBOL SUDAH BAYAR, TIDAK ADA TEKS PANJANG -->
<div class="popup-qr" id="popupQR">
  <div class="qr-panel">
    <h3 id="qrTitle">Dana</h3>
    <div id="qrcode"></div>
    <div class="nomor-qr" id="qrNomor">0838 7216 1233</div>
    <button class="btn-kembali" onclick="tutupQR()">◀ Kembali</button>
  </div>
</div>

<footer>
  🧊 FRESH BREW DRINK — 2026  <span class="no-wa-badge">📞 0838 7216 1233</span>
</footer>

<script>
  // ========== MENU ==========
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
    { nama: "Lychee Tea", harga: 13000, gambar: "https://images.unsplash.com/photo-1556679343-c1c1c1d56c6d?w=700&bri=1.1&q=80" },
    { nama: "Mango Smoothie", harga: 18000, gambar: "https://images.unsplash.com/photo-1558640479-8242c0c8b9b9?w=700&bri=1.2&q=80" },
    { nama: "Taro Latte", harga: 15000, gambar: "https://images.unsplash.com/photo-1604908176997-125f25cc6f3d?w=700&bri=0.95&q=80" }
  ];

  // ========== VARIABEL ==========
  let cart = [];
  const WA_TOKO = "6283872161233";  // NOMOR TOKO (PT)
  let selectedMethod = "";

  // ========== RENDER MENU ==========
  function renderMenu() {
    let html = "";
    menu.forEach((item, idx) => {
      html += `<div class="menu-card">
        <img src="${item.gambar}" alt="${item.nama}" loading="lazy">
        <h3>${item.nama}</h3>
        <p class="price-tag">💰 Rp ${item.harga.toLocaleString()}</p>
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
  window.bukaPopupMetode = function() {
    const nama = document.getElementById("namaPemesan").value.trim();
    if (nama === "") {
      alert("✋ Isi nama pemesan terlebih dahulu!");
      return;
    }
    if (cart.length === 0) {
      alert("🛒 Keranjang masih kosong!");
      return;
    }
    document.getElementById("popupMetode").style.display = "flex";
  };

  window.tutupPopupMetode = function() {
    document.getElementById("popupMetode").style.display = "none";
  };

  // ========== PROSES METODE ==========
  window.prosesMetode = function(metode) {
    selectedMethod = metode;
    tutupPopupMetode();

    if (metode === "Cash") {
      // CASH: LANGSUNG WA KE TOKO
      kirimWaKeToko(metode);
    } else {
      // E-WALLET: TAMPILKAN QR + OTOMATIS WA KE TOKO
      tampilkanQR(metode);
      kirimWaKeToko(metode);
    }
  };

  // ========== TAMPILKAN QR - MURNI QR + NOMOR ==========
  function tampilkanQR(metode) {
    // Bersihkan QR
    document.getElementById("qrcode").innerHTML = "";
    
    // Set judul dan nomor
    let title = "";
    if (metode === "Dana") title = "💙 Dana";
    else if (metode === "OVO") title = "💜 OVO";
    else if (metode === "GoPay") title = "💚 GoPay";
    else if (metode === "ShopeePay") title = "🛒 ShopeePay";
    else title = metode;
    
    document.getElementById("qrTitle").innerText = title;
    document.getElementById("qrNomor").innerText = "0838 7216 1233";

    // Isi QR Code - HANYA NOMOR + METODE
    let qrText = `${metode}: 083872161233`;
    if (metode === "Dana") qrText = "DANA: 083872161233";
    else if (metode === "OVO") qrText = "OVO: 083872161233";
    else if (metode === "GoPay") qrText = "GOPAY: 083872161233";
    else if (metode === "ShopeePay") qrText = "SHOPEEPAY: 083872161233";

    new QRCode(document.getElementById("qrcode"), {
      text: qrText,
      width: 230,
      height: 230,
      colorDark: "#0e523a",
      colorLight: "#ffffff",
      correctLevel: QRCode.CorrectLevel.H
    });

    // Tampilkan popup QR
    document.getElementById("popupQR").style.display = "flex";
  }

  // ========== KIRIM WA KE TOKO ==========
  function kirimWaKeToko(metodeBayar) {
    const nama = document.getElementById("namaPemesan").value.trim();
    let detail = "";
    let total = 0;

    cart.forEach(item => {
      detail += `• ${item.nama} - Rp ${item.harga.toLocaleString()}%0A`;
      total += item.harga;
    });

    let pesan = `🧊 *FRESH BREW - PESANAN BARU*%0A%0A`;
    pesan += `👤 *Nama:* ${nama}%0A`;
    pesan += `📋 *Pesanan:*%0A${detail}%0A`;
    pesan += `💵 *Total:* Rp ${total.toLocaleString()}%0A`;
    pesan += `💳 *Metode:* ${metodeBayar}%0A`;
    
    if (metodeBayar !== "Cash") {
      pesan += `✅ *Pembayaran via ${metodeBayar}*%0A`;
      pesan += `📱 Nomor: 083872161233%0A`;
    }
    
    pesan += `📍 *Lokasi:* Jl. Ir Soetami (Depan Pom Bensin)%0A`;
    pesan += `⏱️ Segera proses pesanan.`;

    window.open(`https://wa.me/${WA_TOKO}?text=${pesan}`, '_blank');
  }

  // ========== TUTUP POPUP QR ==========
  window.tutupQR = function() {
    document.getElementById("popupQR").style.display = "none";
    document.getElementById("qrcode").innerHTML = "";
  };

  // ========== CLICK OUTSIDE ==========
  window.onclick = function(e) {
    const popMethod = document.getElementById("popupMetode");
    const popQR = document.getElementById("popupQR");
    if (e.target === popMethod) popMethod.style.display = "none";
    if (e.target === popQR) {
      popQR.style.display = "none";
      document.getElementById("qrcode").innerHTML = "";
    }
  };

  // ========== INIT ==========
  renderMenu();
  updateCart();
</script>

</body>
</html>
