# Writing Week 1 Frontend Bootcamp
## React JS
**Sebenarnya apasih node itu?**
Jadi yang Namanya web browser, di dalamnya mempunyai mesin Javascript. Masing-masing web browser mesinnya beda”. Kalau di google chrome menggunakan mesin yang bernama V8. Dan mesin itu yang bertugas untuk menjalankan Javascript. Tetapi kita membutuhkan file HTML terlebih dahulu agar bisa memasang Javascriptnya, karena JS hanya bisa berjalan di web browser.

Seiring berjalannya waktu, JS bisa dijalankan di luar web browser dengan bantuan *NodeJS*. Di dalam NodeJS juga ada V8 engine juga sehingga bisa menjalankan JS.

**React adalah** sebuah library untuk membuat tampilan sebuah website. Menggunakan react JS akan mempermudah dan mempercepat proses pembuatan website.

Install react dengan cara ketikkan ``create-react-app nama-project`` pada command prompt. Library” untuk membuat tampilan ini menggunakan teknologi yang menggunakan SPA (single page application). Pada model traditional semisal kita ingin menampilkan halaman home maka kita harus mrnyiapkan page home nya, mau nampilin halaman about maka harus bikin about.html dan seterusnya. Jadi harus nyiapin file html satu per satu. Sedangkan kalua menggunakan SPA kita hanya menggunakan satu file html. Dia akan mengganti isi di dalamnya menggunakan JS. Semisal ingin menapilkan home, kita cukup menyiapkan tampilan homenya saja tanpa membuat file html.

React untuk berinteraksi dengan DOM menggunakan yang Namanya virtual DOM. Virtual DOM bisa dibilang kaya replica atau copyan dari DOM yang asli. 

Perbedaan real DOM dengan virtual DOM. Ketika menggunakan real DOM semisal akan menambahkan element baru itu akan merender note secara keseluruhan. Dan akhirnya membuat yang namanya virtual DOM untuk mempercepat proses perubahan data yang ada di dalam websitenya. Kalua menggunakan virtual DOM, misalnya ada perubahan di dalam DOM maka dia akan melakukan render hanya pada note yang dirubah.

**React Component**

React component adalah salah satu cara untuk mebagi UI dalam satuan-satuan kecil agar terlihat lebih simple dan bisa digunakan Kembali di tempat-tempat yang lain. Semisal kita membuat navbar kita hanya mengcoding sekali dan bisa digunakan di banyak tempat.

Kalau memakai react ada beberapa poin utama: 
1. pembuatan function harus menggunakan huruf besar/kapital, kalau menggunakan huruf kecil nanti akan terjadi error. 
2. Dan juga harus ada return. Dan setelahnya baru bebas mengcoding HTML. 
3. Dalam react hanya boleh punya 1 parent utama. Harus punya pembungkus utama untuk membungkus semua element HTML yang kita punya. Bisa menggnakan ``<></>`` atau ``<div></div>``.

contoh:
```bash
function App() {

    return (
        <div>
            <h1>Hallo</h1>
        </div>
    )
};

export default App;
```

**Memberi image**
gunakan code seperti di bawah ini:
```bash
function App() {

    return (
        <div>
            <img src="" alt=""/>
        </div>
    )
};

export default App;
```

Kemudian untuk mengatur styling image dapat menggunakan CSS. Kalau di react, pertama kita buat file CSSnya bebas dimana, kemudian diimport CSSnya ke dalam react nya. Caranya menggunakan code ``import "./App.css";``. Penempatannya bisa di baris paling atas codingan.

Di react jika ingin membuat class bukan dengan ``class=""`` tetapi dengan ``className=""``. Class bebas diberi nama apa aja untuk nanti kita panggil di file CSSnya. Kemudian tinggal styling pada file CSS seperti biasa.
