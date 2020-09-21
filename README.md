# README
With Docker (Recommended)
0. Ensure Docker is running on your system. Allocate at least 0.5 to 1 GB of
memory in the settings. Allocating more CPU cores will also greatly speed up
build times.
1. Clone the repository/zipped files to your machine and open a terminal session in
the project directory.
2. Run docker-compose build and grab a cup of tea, the web container will
take awhile to complete.
3. Run docker-compose up
a. This will start up the main web container serving the application as well as
other dependencies such as the database and a Redis server.
4. Open a new terminal window and run docker-compose run web rake
db:create db:migrate
a. This will initialize the database used by the application
b. Once this has completed, run docker-compose run web rake
db:seed to create an admin user
5. The website should now be accessible at http://localhost:3000 and the admin
interface should be accessible at http://localhost:3000/admin/login
a. Admin username: admin@example.com Password: password

Without Docker
1. Ensure that you have Ruby (~> 2.5.8), Rails (~> 5.2.4), and Postgres installed on
your system. A local Postgres server should also be running. Note that the
project is configured with a default username/password for Postgres, see
`config/database.yml`
2. Run bundle install and then rake db:migrate in the project root folder
3. Run bundle exec rails s -p 3000 -b '0.0.0.0' to start the server
