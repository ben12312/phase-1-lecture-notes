## Setup app
- npm init -y
- npm i sequelize pg
- npm i -D sequelize-cli
- gitignore node_modules

## Setup Sequelize
- npx sequelize-cli/sequelize init
- ubah config.json
- npx sequelize db:create

## Buat model
- npx sequelize model:generate --name Employee --attributes name:string,role:string
- npx sequelize model:generate --name EmployeeSkill --attributes employeeId:integer,skillId:integer,experienceInYears:integer
- npx sequelize model:generate --name Skill --attributes name:string

## Edit file migrasi model
- kasih referensi untuk setiap foreign key 
    -> coba google "migration foreign key sequelize"

## Migrasi model
- npx sequelize db:migrate

## Kalau lupa ngasih reference di migrasi model
- npx sequelize migration:generate --name add-fk-to-skillId-in-employeeSkills
- di file migrasi baru tambah addConstraint di foreign key yang kelupaan 
    -> coba cek dokumentasi sequelize untuk addConstraint foreign key
- npx sequelize db:migrate

## Tambah asosiasi di model
- cek dokumentasi sequelize untuk asosiasi many to many

## Seed data
- npx sequelize seed:generate --name seed-employee-skills
- npx sequelize seed:generate --name seed-employees
- npx sequelize seed:generate --name seed-skills
- baca file, ditambahin createdAt & updatedAt, hapus id
- bulkInsert (up), bulkDelete (down)
- npx sequelize db:seed:all
    -> notes: bisa error kalau tabel tengahnya di seed duluan, tabel yang dijadikan referensi harus dibuat duluan

## Querying menggunakan include
- coba google "sequelize eager loading"