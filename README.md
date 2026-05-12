**a. What is amqp?**
AMQP adalah protokol standar terbuka di application layer untuk message-oriented middleware. Protokol ini menyediakan fitur seperti message orientation, queuing, routing, reliability, dan security.

**b. What does it mean? guest:guest@localhost:5672**
'guest' yang pertama adalah username default untuk masuk ke RabbitMQ. 'guest' yang kedua adalah password default untuk user tersebut. 'localhost:5672' adalah alamat host dan port tempat message broker RabbitMQ berjalan dan mendengarkan koneksi AMQP yang masuk.

![Slow Subscriber Queue](slow.png)
Karena kita menambahkan jeda waktu 1 detik ('thread::sleep') pada logika pemrosesan subscriber, program tersebut hanya mampu memproses satu pesan per detik. Saat publisher mengirimkan banyak pesan secara instan, pesan-pesan yang belum tertangani akan menumpuk di dalam antrean RabbitMQ, menciptakan backlog sampai subscriber yang lambat tersebut secara bertahap memproses dan mengosongkannya satu per satu.