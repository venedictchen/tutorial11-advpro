1.  Compare the application logs before and after you exposed it as a Service. Try to open the app several times while the proxy into the Service is running. What do you see in the logs? Does the number of logs increase each time you open the app?
- Sebelum aplikasi diekspos sebagai service, log aplikasi hanya menampilkan pesan yang menunjukkan bahwa server HTTP telah dimulai dan mendengarkan di port 8080, server UDP telah dimulai dan mendengarkan di port 8081. Setelah aplikasi diekspos sebagai service, kita dapat berinteraksi dan berkomunikasi dengan server dari luar klaster Kubernetes. Ketika Anda membuka aplikasi beberapa kali dengan proxy ke layanan yang berjalan, log akan bertambah besar. Ini karena server memiliki fungsi logging yang mencatat setiap permintaan HTTP yang masuk beserta stempel waktunya. Setiap kali aplikasi dibuka, permintaan HTTP dikirim ke server, memicu log untuk mencatat pesan tambahan.


2. Notice that there are two versions of `kubectl get` invocation during this tutorial section. The first does not have any option, while the latter has `-n` option with value set to `kube-system`. What is the purpose of the `-n` option and why did the output not list the pods/services that you
explicitly created?
- Selama bagian tutorial ini, terdapat dua versi perintah kubectl get. Yang pertama digunakan tanpa opsi apa pun, sedangkan yang kedua menggunakan opsi -n dengan nilai yang disetel ke kube-system. Flag -n berarti namespace, jadi perintah kubectl get pods,services -n kube-system mengambil semua pod dan layanan dalam namespace 'kube-system'. Layanan dan pod sebelumnya berada di namespace yang berbeda ('default'), itulah sebabnya layanan/pod yang telah dibuat sebelumnya tidak muncul di output.