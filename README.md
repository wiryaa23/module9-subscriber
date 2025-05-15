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
