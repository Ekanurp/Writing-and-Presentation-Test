# Writing Week 2 Frontend Bootcamp
## React JS lannjutan - Proptypes
Prop Types merupakan sebuah lib yang dapat membantu memeriksa data props yang dikirim agar sesuai dengan ekspektasi.

Dengan berkembangnya aplikasi kita, kit dapat menemukan banyak kesalahan atau bugs dengan pengecekan tipe data. Untuk beberapa aplikasi, kita dapat menggunakan ekstensi JavaScript seperti Flow atau TypeScript untuk melakukan pengecekan tipe data di aplikasi secara menyeluruh. Meskipun kita tidak menggunakannya, React memiliki kemampuan pengecekan tipe data. Untuk menjalankan pengecekan terhadap props disebuah komponen, kita dapat menggunakan properti khusus propTypes:

```bash
import PropTypes from 'prop-types';

class Greeting extends React.Component {
  render() {
    return (
      <h1>Hello, {this.props.name}</h1>
    );
  }
}

Greeting.propTypes = {
  name: PropTypes.string
};
```

Dalam contoh ini, kita menggunakan class component, tapi fungsionalitas yang sama dapat juga diterapkan kepada function component, atau komponen yang dibuat dengan ``React.memo`` atau ``React.forwardRef``.

PropTypes mengirimkan berbagai jenis validator yang dapat digunakan untuk memastikan bahwa data yang diterima valid. Contoh diatas, menggunakan PropTypes.string. Ketika nilai yang dikirimkan untuk sebuah prop keliru, sebuah peringatan akan muncul di konsol JavaScript. Untuk alasan performa, propTypes hanya melakukan pengecekan di mode pengembangan atau development.

## React Router
Routing adalah proses di mana pengguna diarahkan ke halaman yang berbeda berdasarkan tindakan atau permintaan mereka. Router ReactJS terutama digunakan untuk mengembangkan Aplikasi Web Halaman Tunggal. React Router digunakan untuk menentukan beberapa rute dalam aplikasi. Saat pengguna mengetik URL tertentu ke browser, dan jika jalur URL ini cocok dengan ‘rute’ apa pun di dalam file router, pengguna akan diarahkan ke rute tersebut.

React Router adalah sistem perpustakaan standar yang dibangun di atas React dan digunakan untuk membuat perutean di aplikasi React menggunakan Paket React Router. Ini menyediakan URL sinkron di browser dengan data yang akan ditampilkan di halaman web. Ini memelihara struktur standar dan perilaku aplikasi dan terutama digunakan untuk mengembangkan web Single Page Application.

Sebelum menggunakan React Router di web, kita perlu menjalankan ``npm i react-router-dom `` untuk menginstall React Router. Library ini secara khusus menginstall versi DOM dari React Router. Jika kita menggunakan React Native, harus menggunkan ``react-router-native`` sebagai gantinya. Selain perbedaan ini, library bekerja hampir sama persis.

- ## Konfigurasi Router
    Langkah selanjutnya yaitu menyiapkan router kita. Yang perlu dilakukan yaitu mengimpor router khusus yang kita butuhkan (BrowserRouter untuk web dan NativeRouter untuk seluler) dan membungkus seluruh aplikasi kita di router tersebut.

    ```bash
    import { BrowserRouter } from "react-router-dom"

    const root = ReactDOM.createRoot(document.getElementById("root"))
    root.render(
        <React.StrictMode>
            <BrowserRouter>
                <App />
            </BrowserRouter>
        </React.StrictMode>
    )
    ```

    Umumnya router diimport di halaman index.jsx pada aplikasi kita dan itu akan membungkus komponen aplikasi kita. Router bekerja seperti context di React dan menyediakan semua informasi yang diperlukan untuk aplikasi kita sehingga kita dapat melakukan routing dan menggunakan semua custom hooks dari React Router.

- ## Mendefinisikan Routes
    Langkah selanjutnya di React Router adalah mendefinisikan routes. Ini biasanya dilakukan di tingkat atas aplikasi kita, seperti di komponen Aplikasi, tetapi dapat dilakukan di mana pun kita mau.

    ```bash
    import { Route, Routes } from "react-router-dom"
    import { Home } from "./Home"
    import { BookList } from "./BookList"

    export function App() {
    return (
        <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/books" element={<BookList />} />
        </Routes>
    )
    }
    ```
    Mendefinisikan routes semudah mendefinisikan satu komponen Routes untuk setiap route dalam aplikasi kita dan kemudian menempatkan semua komponen Route tersebut dalam satu komponen Routes. Setiap kali URL berubah, React Router akan melihat routes yang ditentukan dalam komponen Routes kita dan itu akan merender konten di elemen prop dari Route yang memiliki jalur yang cocok dengan URL. Dalam contoh di atas jika URL kita adalah /books maka komponen BookList akan dirender.

    Hal yang menyenangkan tentang React Router adalah ketika kita menavigasi antar halaman, itu hanya akan menyegarkan konten di dalam komponen Routes kita. Semua konten lainnya di halaman kita akan tetap sama yang membantu kinerja dan pengalaman pengguna.

- ## Handling Navigation
    Langkah terakhir untuk React Router adalah handling navigation. Biasanya dalam sebuah aplikasi kita akan menavigasi dengan anchor tag, tetapi React Router menggunakan Link component kustomnya sendiri untuk handle navigation. Link component ini hanyalah pembungkus di sekitar anchor tag yang membantu memastikan semua routing dan conditional rendering ditangani dengan benar sehingga kita dapat menggunakannya seperti halnya anchor tag biasa.

    ```bash
    import { Route, Routes, Link } from "react-router-dom"
    import { Home } from "./Home"
    import { BookList } from "./BookList"

    export function App() {
    return (
        <>
        <nav>
            <ul>
            <li><Link to="/">Home</Link></li>
            <li><Link to="/books">Books</Link></li>
            </ul>
        </nav>

        <Routes>
            <Route path="/" element={<Home />} />
            <Route path="/books" element={<BookList />} />
        </Routes>
        </>
    )
    }
    ```

    Dalam contoh, penambahan dua tautan ke halaman home dan books. Penggunaan to prop untuk mengatur URL alih-alih href prop yang biasa kita gunakan dengan tag anchor. Ini adalah satu-satunya perbedaan antara Link component dan anchor tag dan merupakan sesuatu yang perlu diingat, karena merupakan kesalahan yang mudah untuk secara tidak sengaja menggunakan href prop alih-alih to prop.

    Hal lain yang perlu diperhatikan adalah bahwa nav yang dibuat di bagian atas halaman berada di luar komponen Routes yang berarti ketika mengubah halaman, bagian nav ini tidak akan dirender ulang karena hanya konten di komponen Routes akan berubah ketika URL berubah.

## State Management React Redux
Redux adalah salah satu state management yang sangat hype pada waktunya dan masih relevan sampai sekarang. Redux juga menawarkan tools untuk masing-masing browser contoh chrome redux devtools untuk memonitor keadaan state kita saat ini. Package middleware-nya juga sudah banyak dikembangkan gratis dan siap digunakan untuk memudahkan kita mengembangkan aplikasi yang kita sedang kerjakan.

Sebagian besar library, seperti React dan Angular dibangun agar komponen dapat mengelola statusnya secara internal tanpa memerlukan pustaka atau alat eksternal. Hal ini pun berfungsi dengan baik untuk aplikasi dengan sedikit komponen, tetapi saat aplikasi semakin bertumbuh menjadi besar, mengelola status yang dibagikan di seluruh komponen menjadi tugas.

Di sinilah Redux hadir. Ia berfungsi untuk melakukan perubahan state yang dibutuhkan oleh setiap fungsional yang ada di suatu aplikasi. Redux adalah library JavaScript yang dikhususkan untuk back-end, di mana Redux sendiri telah berkolaborasi dengan React Native. Oleh karena itu beberapa orang menyebutnya sebagai Redux React.

- ## Beberapa istilah dalam redux
    1. Action
        Action merupakan suatu event, di mana ia adalah satu-satunya cara kita dapat mengirim data dari aplikasi kita ke Redux Store. Data tersebut pun dapat berasal dari interaksi pengguna, panggilan API (API request), atau bisa juga pengiriman formulir. Action ini pun dikirim menggunakan metode ‘store.dispatch ()’.

        Action sendiri merupakan objek JavaScript biasa dan harus memiliki tipe properti (property type) untuk menunjukan jenis action yang akan dilakukan. Selain itu, Action harus memiliki muatan yang berisi informasi yang harus dikerjakan oleh action tersebut.
    2. Reducer
        Function yang menerima object state dan object action, bertugas menentukan bagaimana suatu state diubah. Output reducer adalah state baru.

        Syntax: ``(state, action) => newState``
    3. Store
        Tempat dimana global state disimpan.
    4. Dispatch
        Satu-satunya cara untuk mengubah state di dalam store adalah dengan memanggil method bernama dispatch yang berisi object action, kemudian Redux akan mengeksekusi reducer yang sesuai.
    5. Selector
        Function yang digunakan untuk mendapatkan data dari state yang ada di dalam store.

## Async Actions with Middleware and Thunk
Secara asal, aksi Redux dikirimkan secara sinkron, yang menjadi masalah bagi aplikasi nontrivial yang perlu berkomunikasi dengan API eksternal atau melakukan efek samping. Redux juga memungkinkan pengiriman middleware yang berada di antara aksi dan aksi mencapai reducer.

Ada dua pustaka middleware yang sangat populer yang memungkinkan efek samping dan akses asinkron: Redux Thunk dan Redux Saga.

Thunk adalah konsep pemrograman yang menggunakan fungsi untuk menunda evaluasi/kalkulasi suatu operasi.

Redux Thunk adalah middleware yang memungkinkan kita memanggil pembuat aksi yang mengembalikan fungsi sebagai ganti objek aksi. Fungsi itu menerima metode pengiriman penyimpanan, yang kemudian digunakan untuk mengirim aksi sinkron di dalam isi fungsi setelah operasi asinkron selesai.

- ## Menggunakan Middleware untuk Mengaktifkan Logika Async
    beberapa contoh bagaimana middleware dapat memungkinkan kita untuk menulis semacam logika asinkron yang berinteraksi dengan Redux store.

    Salah satu kemungkinan adalah menulis middleware yang mencari jenis tindakan tertentu, dan menjalankan logika asinkron ketika melihat tindakan tersebut, seperti contoh berikut:
    ```bash
    import { client } from '../api/client'

    const delayedActionMiddleware = storeAPI => next => action => {
    if (action.type === 'todos/todoAdded') {
        setTimeout(() => {
        // Delay this action by one second
        next(action)
        }, 1000)
        return
    }

    return next(action)
    }

    const fetchTodosMiddleware = storeAPI => next => action => {
    if (action.type === 'todos/fetchTodos') {
        // Make an API call to fetch todos from the server
        client.get('todos').then(todos => {
        // Dispatch an action with the todos we received
        storeAPI.dispatch({ type: 'todos/todosLoaded', payload: todos })
        })
    }

    return next(action)
    }
    ```

- ## Redux Async Data Flow
    Jadi bagaimana logika middleware dan async mempengaruhi keseluruhan aliran data aplikasi Redux?

    Sama seperti tindakan normal, pertama-tama kita harus menangani peristiwa pengguna di aplikasi, seperti mengklik tombol. Kemudian memanggil dispatch(), dan meneruskan sesuatu, apakah itu objek tindakan biasa, fungsi, atau nilai lain yang dapat dicari oleh middleware.

    Setelah nilai yang dikirim mencapai middleware, itu dapat membuat panggilan async, dan kemudian mengirimkan objek tindakan nyata saat panggilan async selesai.

- ## Menggunakan Redux Thunk Middleware
    Ternyata, Redux sudah memiliki versi resmi dari "async function middleware", yang disebut middleware Redux "Thunk". Middleware thunk memungkinkan kita untuk menulis fungsi yang mendapatkan ``dispatch`` dan ``getState`` sebagai argumen. Fungsi thunk dapat memiliki logika asinkron yang kita inginkan di dalamnya, dan logika tersebut dapat mengirimkan tindakan dan membaca status penyimpanan sesuai kebutuhan.

    **Konfigurasi store**
    Install package redux-thunk dengan ``npm install redux-thunk``.

    Setelah terinstall kita dapat update Redux store pada todo app untuk menggunakan middleware:
    ```bash
    import thunkMiddleware from 'redux-thunk'

    const composedEnhancer = composeWithDevTools(applyMiddleware(thunkMiddleware))
    ```

    **Fetching todo dari server**
    Saat ini entri todo hanya dapat ada di browser klien. Kita membutuhkan cara untuk memuat daftar todos dari server saat aplikasi dijalankan.

    Mulai dengan menulis fungsi thunk yang membuat panggilan AJAX ke titik akhir /fakeApi/todos untuk meminta array objek todo, dan kemudian mengirimkan tindakan yang berisi array itu sebagai payload. Karena ini terkait dengan fitur todos secara umum, kita akan menulis fungsi thunk di file todosSlice.js:
    ```bash
    export async function fetchTodos(dispatch, getState) {
        const response = await client.get('/fakeApi/todos')
        dispatch({ type: 'todos/todosLoaded', payload: response.todos })
    }
    ```

    Kita hanya ingin membuat panggilan API ini sekali, saat aplikasi dimuat untuk pertama kalinya. Ada beberapa tempat kita bisa menempatkan ini:

    1. Di komponen ``<App>``, di ``useEffect`` hook
    2. Dalam komponen ``<TodoList>``, dalam ``useEffect`` hook
    3. Di file ``index.js`` langsung, tepat setelah kita mengimpor store

    Untuk saat ini, mari kita coba menempatkan ini langsung di index.js:

    ```bash
    import store from './store'
    import { fetchTodos } from './features/todos/todosSlice'

    store.dispatch(fetchTodos)
    ```