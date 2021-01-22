## Sequelize initialization flow

### **Setup**

1. Inisialisasi project

    > npm init -y

2. Install packages yang diperlukan

    > npm i sequelize pg

3. Install CLI Sequelize sebagai development dependency

    > npm i -D sequelize-cli

4. Inisialisasi Sequelize

    > npx sequelize init

5. Edit config.json (sesuaikan dengan setting database kalian)

6. Buat database

    > npx sequelize db:create

### **Model & migration**

7. Buat model

    > npx sequelize model:generate
    >
    > --name \<ModelName> (contoh >> Pokemon -> PascalCase & Singular)
    >
    > --attributes \<attr1:datatype,attr2:datatype,...> (contoh >> name:string,hp:integer,... -> tanpa spasi dan dipisahkan dengan koma)

8. Pastikan kalau async await di file migration diubah ke promise terlebih dahulu (return promise)

9. Migrate untuk melakukan perubahan ke database

    > npx sequelize db:migrate

10. Bagaimana kalau masih ada yang mau diubah di database? Buat file migrasi baru

    >  npx sequelize migration:generate --name <deskripsi-action> (contoh >> add-column-speed-to-pokemon)
    >
    > -> setelah digenerate, kembali ke step 8 & 9

11. Pastikan queryInterface yang digunakan di file migrasi sesuai (cek [list queryInterface](https://sequelize.org/v5/class/lib/query-interface.js~QueryInterface.html))

11. Bagaimana kalau mau membatalkan migrasi? Bisa di-undo

    > npx sequelize db:migrate:undo

### **Seeding**

12. Buat file seed

    > npx sequelize seed:generate --name <deskripsi-action>

13. Seed ke database

    > npx sequelize db:seed --seed <file-seed-yg-mana>

### **Usage**

14. Ambil model pakai require

15. Panggil model dengan Model.method().then().catch()

    > contoh: Pokemon.findAll().then().catch()
    >
    > -> Lebih lanjut, bisa cek [model methods list](https://sequelize.org/v5/class/lib/model.js~Model.html) dan [common usage](https://sequelize.org/v5/manual/models-usage.html)

### **Main reference**

- [Dokumentasi Sequelize v5](https://sequelize.org/v5/)