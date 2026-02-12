
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Fresh Brew Drink</title>

<style>

body{
    font-family:Segoe UI;
    margin:0;
    background:linear-gradient(to right,#1d2b64,#f8cdda);
    color:#333;
}

header{
    text-align:center;
    padding:25px;
    color:white;
}

.container{
    padding:20px;
}

.menu{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:20px;
}

.card{
    background:white;
    border-radius:15px;
    overflow:hidden;
    box-shadow:0 5px 15px rgba(0,0,0,0.2);
    transition:0.3s;
}

.card:hover{
    transform:scale(1.05);
}

.card img{
    width:100%;
    height:180px;
    object-fit:cover;
}

.card h3{
    margin:10px;
}

.price{
    margin:10px;
    color:#27ae60;
    font-weight:bold;
}

button{
    background:#2c3e50;
    color:white;
    border:none;
    padding:10px 15px;
    border-radius:8px;
    margin:10px;
    cursor:pointer;
}

button:hover{
    background:#34495e;
}

.cart{
    background:white;
    padding:20px;
    border-radius:15px;
    margin-top:30px;
}

input{
    padding:10px;
    width:100%;
    margin-bottom:10px;
    border-radius:8px;
    border:1px solid #ccc;
}

/* popup */
.popup{
    position:fixed;
    top:0;
    left:0;
    width:100%;
    height:100%;
    background:rgba(0,0,0,0.6);
    display:none;
    justify-content:center;
    align-items:center;
}

.popup-content{
    background:white;
    padding:30px;
    border-radius:15px;
    text-align:center;
}

footer{
    text-align:center;
    color:white;
    padding:20px;
}

</style>
</head>

<body>

<header>
<h1>☕ Fresh Brew Drink</h1>
<p>Pesan Minuman Segar Online</p>
</header>

<div class="container">

<h2>Menu Minuman</h2>
<div class="menu" id="menuList"></div>

<div class="cart">
<h2>🛒 Keranjang</h2>

<input type="text" id="namaPemesan" placeholder="Masukkan Nama Pemesan">

<ul id="cartList"></ul>
<h3 id="totalHarga"></h3>

<button onclick="bukaPembayaran()">Bayar</button>
</div>

<h2>📍 Lokasi</h2>
<p>Jl. Ir Soetami Depan Pom Bensin</p>

<iframe 
src="https://maps.google.com/maps?q=Jl.%20Ir.%20Soetami&t=&z=15&ie=UTF8&iwloc=&output=embed"
width="100%" height="300"></iframe>

</div>

<!-- Popup pembayaran -->
<div class="popup" id="popupBayar">
<div class="popup-content">
<h2>Pilih Metode Pembayaran</h2>

<button onclick="checkout('Cash')">Cash</button>
<button onclick="checkout('Dana')">Dana</button>
<button onclick="checkout('OVO')">OVO</button>
<button onclick="checkout('GoPay')">GoPay</button>
<button onclick="checkout('ShopeePay')">ShopeePay</button>

<br><br>
<button onclick="tutupPopup()">Tutup</button>

</div>
</div>

<footer>
© 2026 Fresh Brew Drink
</footer>

<script>

let menu = [

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

let cart=[];

function tampilMenu(){
let html="";
menu.forEach((m,i)=>{
html+=`
<div class="card">
<img src="${m.gambar}">
<h3>${m.nama}</h3>
<p class="price">Rp ${m.harga}</p>
<button onclick="tambah(${i})">Keranjang</button>
</div>`;
});
document.getElementById("menuList").innerHTML=html;
}

function tambah(index){
cart.push(menu[index]);
tampilKeranjang();
}

function tampilKeranjang(){

let html="";
let total=0;

cart.forEach(c=>{
html+=`<li>${c.nama} - Rp ${c.harga}</li>`;
total+=c.harga;
});

document.getElementById("cartList").innerHTML=html;
document.getElementById("totalHarga").innerText="Total: Rp "+total;
}

function bukaPembayaran(){

let nama=document.getElementById("namaPemesan").value;

if(nama==""){
alert("Masukkan nama pemesan!");
return;
}

if(cart.length==0){
alert("Keranjang kosong!");
return;
}

document.getElementById("popupBayar").style.display="flex";
}

function tutupPopup(){
document.getElementById("popupBayar").style.display="none";
}

function checkout(metode){

let nama=document.getElementById("namaPemesan").value;
let pesan=`Halo, saya ${nama} ingin pesan:%0A`;
let total=0;

cart.forEach(c=>{
pesan+=`${c.nama} - Rp ${c.harga}%0A`;
total+=c.harga;
});

pesan+=`Total: Rp ${total}%0A`;
pesan+=`Metode Bayar: ${metode}`;

window.open(`https://wa.me/6283872161233?text=${pesan}`);
}

tampilMenu();

</script>

</body>
</html>
