# QUESTION

- What is amqp?
> AMQP (Advanced Message Queuing Protocol) adalah protokol komunikasi terbuka yang dirancang untuk message-oriented middleware, yang memungkinkan aplikasi saling bertukar pesan secara aman dan terpisah melalui queue. Protokol ini mendukung antrian pesan, routing yang kompleks, keandalan tinggi, serta komunikasi asynchronous antar sistem yang terpisah. AMQP umum digunakan dalam sistem microservices untuk mengurangi dependency langsung antar layanan sehingga memungkinkan pengiriman dan penerimaan pesan secara asinkron melalui message broker seperti RabbitMQ. AMQP memungkinkan publisher untuk mengirim pesan ke broker, yang kemudian diambil oleh subscriber dari queue.

- What does it mean? guest:guest@localhost:5672 , what is the first guest, and what
  is the second guest, and what is localhost:5672 is for?
> `guest:guest@localhost:5672` adalah format umum untuk menyambung ke broker pesan seperti RabbitMQ melalui protokol AMQP.
> - guest pertama merupakan username yang digunakan untuk login ke broker.
> - guest kedua merupakan password untuk username tersebut.
> - localhost menunjukkan bahwa server RabbitMQ berjalan di computer lokal.
> - 5672 merupakan port default yang digunakan oleh protokol AMQP.

- Simulation Slow Subscriber
![Slow_Subscriber](images/Slow_Subscriber.png)
Gambar tersebut menunjukkan queue yang terbentuk ketika publisher dijalankan secara cepat beberapa kali, padahal subscriber diperlambat dengan delay. Saya menjalankan publisher sebanyak 4 kali sehingga total queue mencapai 20 karena tiap eksekusi mengirim 5 pesan.

- Reflection and Running At Least Three Subscribers
![Three_Subscriber](images/Three_Subscribers.png)
![RabbitMQ_ThreeSubs](images/RabbitMQ_ThreeSubs.png)
  Ketika menjalankan tiga instance subscriber pada tiga terminal terpisah, message dari publisher yang dijalankan beberapa kali terbagi secara merata ke masing-masing subscriber. Hal ini dapat dilihat dari log ketiga terminal yang masing-masing user_id-nya berbeda. Meski begitu, subscriber dalam kasus ini menjadi tidak menerima keseluruhan message yang dikirimkan. Ini dapat menjadi masalah Ketika kita ingin setiap subscriber sama-sama menerima keseluruhan message. Jika ingin meningkatkan hal ini lebih lanjut, system apat menambahkan mekanisme asinkron dengan basis tokio agar subscriber menjadi lebih scalable dalam menangani workload yang besar. 