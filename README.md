
<html lang="id">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Fresh Brew Drink – QR Bayar</title>
  <!-- library untuk generate QR code sederhana -->
  <script src="https://cdn.jsdelivr.net/npm/qrcodejs@1.0.0/qrcode.min.js"></script>
  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: 'Segoe UI', Roboto, system-ui, sans-serif;
      margin: 0;
      /* background lebih fresh, gradasi hangat ke hijau lumut */
      background: linear-gradient(145deg, #0b3b3c 0%, #2b5a4b 40%, #f1e9db 100%);
      color: #1e2f2d;
      min-height: 100vh;
      backdrop-filter: blur(1px);
    }

    header {
      text-align: center;
      padding: 30px 20px;
      color: white;
      text-shadow: 2px 2px 6px #0a1e1c;
      background: rgba(10, 40, 35, 0.45);
      backdrop-filter: blur(6px);
      border-bottom: 2px solid #f9d56e;
    }

    header h1 {
      font-size: 2.8rem;
      letter-spacing: 2px;
      margin-bottom: 8px;
    }

    .container {
      padding: 30px 25px;
      max-width: 1300px;
      margin: 0 auto;
    }

    h2 {
      color: #fef9e6;
      text-shadow: 2px 2px 3px #1e3a2f;
      border-left: 10px solid #f8c150;
      padding-left: 18px;
      margin: 30px 0 20px 0;
      font-weight: 600;
      font-size: 1.9rem;
    }

    /* menu grid */
    .menu {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
      gap: 28px;
    }

    .card {
      background: rgba(255, 255, 245, 0.9);
      backdrop-filter: blur(10px);
      border-radius: 24px;
      overflow: hidden;
      box-shadow: 0 15px 30px -8px rgba(0, 30, 20, 0.4);
      transition: all 0.25s ease;
      border: 1px solid #ffffffb0;
    }

    .card:hover {
      transform: translateY(-8px) scale(1.02);
      box-shadow: 0 25px 35px -6px #1f3a32;
      background: white;
    }

    .card img {
      width: 100%;
      height: 190px;
      object-fit: cover;
      border-bottom: 3px solid #f9d342;
    }

    .card h3 {
      margin: 16px 16px 6px;
      font-size: 1.4rem;
      font-weight: 700;
      color: #1f4e3d;
    }

    .price {
      margin: 5px 16px;
      color: #1e7b4b;
      font-weight: 800;
      font-size: 1.25rem;
      letter-spacing: 0.5px;
    }

    button {
      background: #1f5642;
      color: white;
      border: none;
      padding: 12px 20px;
      border-radius: 60px;
      margin: 16px;
      cursor: pointer;
      font-weight: 600;
      font-size: 1rem;
      transition: 0.15s;
      box-shadow: 0 8px 0 #0b2f24;
      border: 1px solid #b3e0c0;
      width: calc(100% - 32px);
    }

    button:hover {
      background: #2d805e;
      transform: translateY(-3px);
      box-shadow: 0 10px 0 #0b2f24;
    }

    button:active {
      transform: translateY(4px);
      box-shadow: 0 4px 0 #0b2f24;
    }

    /* Keranjang */
    .cart {
      background: #fcf6e8f2;
      backdrop-filter: blur(8px);
      padding: 28px;
      border-radius: 40px 40px 30px 30px;
      margin-top: 40px;
      box-shadow: 0 20px 30px #142d26;
      border: 2px solid #ffd78c;
    }

    .cart h2 {
      color: #1d4a3a;
      border-left: 12px solid #f4b942;
      margin-top: 0;
      text-shadow: none;
    }

    input {
      padding: 14px 18px;
      width: 100%;
      margin-bottom: 20px;
      border-radius: 50px;
      border: 2px solid #c8b18b;
      font-size: 1rem;
      background: #fffcf0;
    }

    #cartList {
      list-style: none;
      background: #efe4ca;
      padding: 18px 22px;
      border-radius: 28px;
      font-weight: 500;
      color: #1f4e3a;
      box-shadow: inset 0 2px 8px #b6a082;
    }

    #cartList li {
      padding: 8px 0;
      border-bottom: 1px dashed #5b7f6a;
      font-size: 1.1rem;
    }

    #totalHarga {
      font-size: 1.9rem;
      color: #1b402e;
      font-weight: 900;
      margin: 18px 0 8px;
      text-align: right;
      background: #fdebcd;
      padding: 15px 25px;
      border-radius: 40px;
    }

    /* popup utama untuk pilihan metode */
    .popup {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(8, 40, 30, 0.8);
      backdrop-filter: blur(5px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 999;
    }

    .popup-content {
      background: #fffef5;
      padding: 30px 35px;
      border-radius: 60px 20px 60px 20px;
      text-align: center;
      max-width: 550px;
      width: 90%;
      border: 5px solid #ffc857;
      box-shadow: 0 30px 40px #041a13;
    }

    .popup-content h2 {
      color: #17503e;
      border-left: none;
      text-shadow: none;
      margin-top: 0;
    }

    /* tombol metode di popup awal */
    .popup-content button {
      display: inline-block;
      width: auto;
      margin: 8px;
      padding: 12px 22px;
      background: #2f5e4c;
      border-radius: 50px;
      font-weight: 700;
      box-shadow: 0 6px 0 #17352b;
    }

    /* area QR code popup (level ke-2) */
    .qr-popup {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background: rgba(0, 20, 15, 0.85);
      backdrop-filter: blur(4px);
      display: none;
      justify-content: center;
      align-items: center;
      z-index: 1000;
    }

    .qr-box {
      background: linear-gradient(145deg, #ffffff, #fff7e6);
      padding: 30px 25px;
      border-radius: 48px;
      text-align: center;
      border: 6px solid #fbdb9c;
      max-width: 420px;
      width: 90%;
      box-shadow: 0 30px 35px #051010;
    }

    .qr-box h3 {
      color: #1f543e;
      font-size: 1.9rem;
      margin-bottom: 8px;
      text-shadow: 2px 2px 0 #ffeab5;
    }

    .qr-box p {
      font-size: 1.2rem;
      background: #1f4d3a;
      color: white;
      padding: 10px;
      border-radius: 100px;
      margin: 15px 0;
      letter-spacing: 2px;
      font-weight: 600;
    }

    #qrcode {
      display: flex;
      justify-content: center;
      margin: 15px 0 10px;
    }

    #qrcode img {
      border-radius: 24px;
      padding: 12px;
      background: white;
      border: 4px solid #256b4b;
    }

    .btn-close-qr {
      background: #c06a3b;
      box-shadow: 0 6px 0 #6f3f24;
      margin-top: 15px;
      padding: 14px 25px;
      font-size: 1.2rem;
    }

    iframe {
      border-radius: 30px;
      border: 4px solid #ffd966;
      margin-top: 15px;
      height: 280px;
    }

    footer {
      text-align: center;
      color: #ffefcf;
      padding: 30px;
      font-size: 1.2rem;
      background: #0a332bb3;
      backdrop-filter: blur(4px);
      margin-top: 50px;
      font-weight: 600;
    }

    /* hiasan tambahan */
    .nomor-wa {
      background: #fbe192;
      padding: 5px 18px;
      border-radius: 50px;
      color: #1f4439;
      font-weight: 700;
    }
  </style>
</head>
<body>

<header>
  <h1>☕ Fresh Brew Drink</h1>
  <p style="font-size:1.4rem; background:#1b4e3ab0; display:inline-block; padding:6px 26px; border-radius:50px;">🌿 segar, kekinian, qr instan</p>
</header>

<div class="container">
  <h2>🍹 Menu Spesial</h2>
  <div class="menu" id="menuList"></div>

  <!-- KERANJANG -->
  <div class="cart">
    <h2>🛒 Keranjang Pesanan</h2>
    <input type="text" id="namaPemesan" placeholder="✏️ Masukkan nama pemesan" autocomplete="off">
    <ul id="cartList"></ul>
    <h3 id="totalHarga">Total: Rp 0</h3>
    <button onclick="bukaPembayaran()" style="background:#b86b2c; font-size:1.3rem; box-shadow:0 8px 0 #6e411b;">💳 Lanjut Bayar</button>
  </div>

  <h2>📍 Lokasi Kami</h2>
  <p style="color:white; font-size:1.3rem; background:#28634ab3; padding:10px 25px; border-radius:60px; display:inline-block;">⛽ Jl. Ir Soetami (Depan Pom Bensin)</p>
  <iframe 
    src="https://maps.google.com/maps?q=Jl.%20Ir.%20Soetami&t=&z=15&ie=UTF8&iwloc=&output=embed"
    width="100%" height="300" style="border:0; border-radius:32px;" allowfullscreen loading="lazy">
  </iframe>
</div>

<!-- POPUP 1: Pilih metode pembayaran (muncul setelah tekan bayar) -->
<div class="popup" id="popupBayar">
  <div class="popup-content">
    <h2 style="font-size:2rem;">💸 Pilih metode</h2>
    <div style="display:flex; flex-wrap:wrap; justify-content:center; gap:12px;">
      <button onclick="pilihMetode('Cash')">💵 Cash</button>
      <button onclick="pilihMetode('Dana')">💙 Dana</button>
      <button onclick="pilihMetode('OVO')">💜 OVO</button>
      <button onclick="pilihMetode('GoPay')">💚 GoPay</button>
      <button onclick="pilihMetode('ShopeePay')">🛒 ShopeePay</button>
    </div>
    <br>
    <button onclick="tutupPopup()" style="background:#7f5b3c; box-shadow:0 6px 0 #4f3925;">✖ Tutup</button>
  </div>
</div>

<!-- POPUP 2: QR Code untuk e-wallet + konfirmasi wa -->
<div class="qr-popup" id="qrPopup">
  <div class="qr-box">
    <h3 id="qrMethodTitle">🧾 Dana</h3>
    <div id="qrcode"></div>
    <p id="qrNumberDisplay">083872161233</p>
    <p style="background:#ffeaa5; color:#215a44; font-size:1.1rem;">📱 scan & bayar • otomatis WA</p>
    <button id="confirmPayBtn" onclick="konfirmasiDanKirimWA()" style="background:#30835c; padding:16px 24px; font-size:1.25rem;">✅ Saya sudah bayar</button>
    <button onclick="tutupQrPopup()" class="btn-close-qr" style="background:#8f5242;">⬅ Kembali</button>
  </div>
</div>

<footer>
  © 2026 Fresh Brew Drink — ☁️ nikmati segarnya 
  <span class="nomor-wa">📞 0838 7216 1233</span>
</footer>

<script>
  // =========== DATA MENU =============
  const menu = [
    {nama:"Es Teh Manis", harga:5000, gambar:"https://images.unsplash.com/photo-1556679343-c1c1c1d56c6d"},
    {nama:"Es Teh Lemon", harga:8000, gambar:"https://images.unsplash.com/photo-1558640479-8242c0c8b9b9"},
    {nama:"Thai Tea", harga:12000, gambar:"https://images.unsplash.com/photo-1604908176997-125f25cc6f3d"},
    {nama:"Matcha Latte", harga:15000, gambar:"https://images.unsplash.com/photo-1572442388796-11668a67e53d"},
    {nama:"Es Kopi Susu", harga:13000, gambar:"https://images.unsplash.com/photo-1509042239860-f550ce710b93"},
    {nama:"Cappuccino", harga:15000, gambar:"https://images.unsplash.com/photo-1511920170033-f8396924c348"},
    {nama:"Americano", harga:12000, gambar:"https://images.unsplash.com/photo-1498804103079-a6351b050096"},
    {nama:"Kopi Gula Aren", harga:14000, gambar:"https://images.unsplash.com/photo-1495474472287-4d71bcdd2085"},
    {nama:"Chocolate Ice", harga:15000, gambar:"https://images.unsplash.com/photo-1572490122747-3968b75cc699"}
  ];

  let cart = [];
  let selectedMethod = "";      // simpan metode yg dipilih (Dana, OVO, dll)
  let waNumber = "6283872161233"; // kode internasional tanpa + / 08, sudah sesuai format

  // =========== RENDER MENU ===========
  function tampilMenu() {
    let html = "";
    menu.forEach((m, i) => {
      html += `
        <div class="card">
          <img src="${m.gambar}" alt="${m.nama}" loading="lazy">
          <h3>${m.nama}</h3>
          <p class="price">Rp ${m.harga.toLocaleString()}</p>
          <button onclick="tambah(${i})">➕ Keranjang</button>
        </div>`;
    });
    document.getElementById("menuList").innerHTML = html;
  }

  window.tambah = function(index) {
    cart.push(menu[index]);
    tampilKeranjang();
  };

  function tampilKeranjang() {
    let html = "";
    let total = 0;
    cart.forEach(c => {
      html += `<li>🍸 ${c.nama}  —  Rp ${c.harga.toLocaleString()}</li>`;
      total += c.harga;
    });
    document.getElementById("cartList").innerHTML = html;
    document.getElementById("totalHarga").innerText = "Total: Rp " + total.toLocaleString();
  }

  // =========== POPUP 1 (METODE) ===========
  window.bukaPembayaran = function() {
    const nama = document.getElementById("namaPemesan").value.trim();
    if (nama === "") {
      alert("✋ Masukkan nama pemesan terlebih dahulu!");
      return;
    }
    if (cart.length === 0) {
      alert("🛒 Keranjang masih kosong, pilih minuman dulu yuk!");
      return;
    }
    document.getElementById("popupBayar").style.display = "flex";
  };

  window.tutupPopup = function() {
    document.getElementById("popupBayar").style.display = "none";
  };

  // =========== PILIH METODE & TAMPILKAN QR (kecuali cash) ===========
  window.pilihMetode = function(metode) {
    selectedMethod = metode;
    const nama = document.getElementById("namaPemesan").value.trim();
    
    // Tutup popup pilihan metode
    tutupPopup();

    if (metode === "Cash") {
      // langsung kirim wa tanpa QR, sesuai permintaan: cash langsung
      kirimWaPesanan(metode);
    } else {
      // e-wallet: TAMPILKAN QR DENGAN NOMOR 083872161233 (ditampilkan di qr & text)
      generateAndShowQr(metode);
    }
  };

  // =========== GENERATE QR & POPUP QR ===========
  function generateAndShowQr(metode) {
    // Bersihkan QR code sebelumnya
    document.getElementById("qrcode").innerHTML = "";

    // nomor tujuan sesuai permintaan: 083872161233, ditampilkan dalam format 0838-7216-1233
    const nomorEwallet = "083872161233";
    const nomorTampil = "0838 7216 1233";  // untuk keperluan display
    
    // Set title sesuai metode
    document.getElementById("qrMethodTitle").innerText = `🧾 ${metode}`;
    document.getElementById("qrNumberDisplay").innerText = nomorTampil;

    // Konten QR: kita buat seperti ID / nomor tujuan, tapi agar jelas kita isi dengan
    // "Bayar ke [metode] : 083872161233" atau bisa langsung nomor.
    // Disarankan tampil dalam format "DANA: 083872161233" dll.
    let qrString = "";
    if (metode === "Dana") qrString = `DANA-ID: 083872161233`;
    else if (metode === "OVO") qrString = `OVO: 083872161233`;
    else if (metode === "GoPay") qrString = `GOPAY: 083872161233`;
    else if (metode === "ShopeePay") qrString = `SHOPEEPAY: 083872161233`;
    else qrString = `${metode}: 083872161233`;

    // Generate QR Code menggunakan library qrcodejs
    new QRCode(document.getElementById("qrcode"), {
      text: qrString,
      width: 210,
      height: 210,
      colorDark: "#0a3f2b",
      colorLight: "#fffce6",
      correctLevel: QRCode.CorrectLevel.H
    });

    // Tampilkan popup QR
    document.getElementById("qrPopup").style.display = "flex";
  }

  // tombol "Saya sudah bayar" di popup QR → kirim WA dengan metode e-wallet
  window.konfirmasiDanKirimWA = function() {
    // pastikan metode terisi (e-wallet)
    if (selectedMethod && selectedMethod !== "Cash") {
      kirimWaPesanan(selectedMethod);
    } else {
      // fallback
      kirimWaPesanan("E-Wallet");
    }
    // setelah WA terkirim, tutup popup QR
    tutupQrPopup();
  };

  // Fungsi Kirim WhatsApp (digunakan cash langsung, atau setelah klik 'saya sudah bayar' pada e-wallet)
  function kirimWaPesanan(metodeBayar) {
    const nama = document.getElementById("namaPemesan").value.trim() || "Pemesan";
    let detailPesanan = "";
    let total = 0;

    cart.forEach(c => {
      detailPesanan += `• ${c.nama} - Rp ${c.harga.toLocaleString()}%0A`;
      total += c.harga;
    });

    const totalRp = `Rp ${total.toLocaleString()}`;
    let pesan = `☕ *Fresh Brew Drink*%0A`;
    pesan += `Halo, saya *${nama}* ingin pesan:%0A`;
    pesan += `${detailPesanan}%0A`;
    pesan += `─────────────────%0A`;
    pesan += `💵 *Total: ${totalRp}*%0A`;
    pesan += `💳 Metode Bayar: *${metodeBayar}*%0A`;
    
    // Jika metode bukan cash, tambah info pembayaran via QR
    if (metodeBayar !== "Cash") {
      pesan += `✅ Sudah melakukan pembayaran via ${metodeBayar} (QR) ke nomor 083872161233.%0A`;
    } else {
      pesan += `💰 Pembayaran Cash (langsung di kasir).%0A`;
    }
    pesan += `📍 Ambil di Jl. Ir Soetami (Depan Pom Bensin)%0A`;
    pesan += `Terima kasih! 🧋✨`;

    // gunakan nomor whatsapp yang sudah ditentukan 083872161233 → 6283872161233
    window.open(`https://wa.me/${waNumber}?text=${pesan}`, '_blank');
  }

  // Tutup popup QR
  window.tutupQrPopup = function() {
    document.getElementById("qrPopup").style.display = "none";
    // bersihkan QR supaya tidak numpuk
    document.getElementById("qrcode").innerHTML = "";
  };

  // Tutup popup metode
  window.tutupPopup = function() {
    document.getElementById("popupBayar").style.display = "none";
  };

  // Extra: jika klik di luar popup QR, bisa tutup (opsional)
  window.onclick = function(event) {
    const qrPop = document.getElementById("qrPopup");
    const methodPop = document.getElementById("popupBayar");
    if (event.target === qrPop) {
      qrPop.style.display = "none";
      document.getElementById("qrcode").innerHTML = "";
    }
    if (event.target === methodPop) {
      methodPop.style.display = "none";
    }
  };

  // inisialisasi menu
  tampilMenu();
  tampilKeranjang(); // keranjang kosong
</script>

<!-- Pastikan QRCode js telah di load, fallback kecil -->
<script>
  // Jika qrcode js gagal load, beri cadangan sederhana (hanya fallback)
  if (typeof QRCode === "undefined") {
    console.warn("QRCode library belum siap, muat ulang atau pakai fallback");
    document.addEventListener("DOMContentLoaded", function() {
      if (typeof QRCode === "undefined") {
        alert("⚠️ Gagal memuat QR. Refresh atau periksa koneksi.");
      }
    });
  }
</script>

</body>
</html>
