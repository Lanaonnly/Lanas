
<html lang="id">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Segar Rasa Cafe</title>

<style>
body{
    font-family:Segoe UI;
    margin:0;
    background:#f4f4f4;
}

header{
    background:#2c3e50;
    color:white;
    padding:20px;
    text-align:center;
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
    border-radius:10px;
    box-shadow:0 2px 8px rgba(0,0,0,0.2);
    overflow:hidden;
    text-align:center;
}

.card img{
    width:100%;
    height:180px;
    object-fit:cover;
}

.card h3{
    margin:10px 0;
}

.price{
    color:#27ae60;
    font-weight:bold;
}

button{
    margin:10px;
    padding:10px 20px;
    border:none;
    background:#3498db;
    color:white;
    border-radius:5px;
    cursor:pointer;
}

button:hover{
    background:#2980b9;
}

.cart{
    background:white;
    margin-top:30px;
    padding:20px;
    border-radius:10px;
}

footer{
    background:#2c3e50;
    color:white;
    text-align:center;
    padding:15px;
    margin-top:30px;
}
</style>
</head>

<body>

<header>
<h1>☕ Segar Rasa Cafe</h1>
<p>Terima Pesanan Minuman Online</p>
</header>

<div class="container">

<h2>Menu Minuman</h2>

<div class="menu" id="menuList"></div>

<div class="cart">
<h2>🛒 Keranjang</h2>
<ul id="cartList"></ul>
<button onclick="checkout()">Selesai & Bayar</button>
</div>

<h2>📍 Lokasi</h2>
<p>Jl. Ir Soetami Depan Pom Bensin</p>

<iframe 
src="https://maps.google.com/maps?q=Jl.%20Ir.%20Soetami&t=&z=15&ie=UTF8&iwloc=&output=embed"
width="100%" height="300"></iframe>

</div>

<footer>
© 2026 Segar Rasa Cafe
</footer>

<script>

let menu = [
{nama:"Es Teh Manis", harga:5000, gambar:"https://images.unsplash.com/photo-1556679343-c1c1c1d56c6d"},
{nama:"Es Teh Lemon", harga:8000, gambar:"https://images.unsplash.com/photo-1558640479-8242c0c8b9b9"},
{nama:"Es Kopi Susu", harga:12000, gambar:"https://images.unsplash.com/photo-1509042239860-f550ce710b93"},
{nama:"Es Cappuccino", harga:15000, gambar:"https://images.unsplash.com/photo-1511920170033-f8396924c348"},
{nama:"Es Kopi Gula Aren", harga:14000, gambar:"https://images.unsplash.com/photo-1495474472287-4d71bcdd2085"}
];

let cart = [];

function tampilMenu(){
    let html="";
    menu.forEach((m,i)=>{
        html+=`
        <div class="card">
            <img src="${m.gambar}">
            <h3>${m.nama}</h3>
            <p class="price">Rp ${m.harga}</p>
            <button onclick="tambahKeranjang(${i})">Keranjang</button>
        </div>
        `;
    });
    document.getElementById("menuList").innerHTML=html;
}

function tambahKeranjang(index){
    cart.push(menu[index]);
    tampilKeranjang();
}

function tampilKeranjang(){
    let list="";
    cart.forEach(c=>{
        list+=`<li>${c.nama} - Rp ${c.harga}</li>`;
    });
    document.getElementById("cartList").innerHTML=list;
}

function checkout(){
    if(cart.length==0){
        alert("Keranjang kosong!");
        return;
    }

    let pesan="Halo, saya ingin pesan:%0A";
    let total=0;

    cart.forEach(c=>{
        pesan+=`${c.nama} - Rp ${c.harga}%0A`;
        total+=c.harga;
    });

    pesan+=`Total: Rp ${total}`;

    window.open(`https://wa.me/6283872161233?text=${pesan}`);
}

tampilMenu();

</script>

</body>
</html>
