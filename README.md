# PostgreSQL Pack - MacOS

- **install PostgreSQL** *(object-relational database system)*
- **install pgadmin 4** *(admin and devplatform for PostgreSQL)*
- **install pgmodeler** *(database modeler)*

### Install PostgreSQL

1) Download postgres on <a href="https://postgresapp.com/downloads.html">postgresapp</a>
2) Move to **Applications** folder
3) Run this app
4) Click "Initialize" to create a new server
5) Configure your $PATH to use the included command line tools (optional):
```bash
sudo mkdir -p /etc/paths.d &&
echo /Applications/Postgres.app/Contents/Versions/latest/bin | sudo tee /etc/paths.d/postgresapp
```

### Install pgadmin 4

1) Go to the most recent version on <a href="https://www.pgadmin.org/download/pgadmin-4-macos/">pgadmin</a> and download the .dmg
2) Move to **Applications** folder
3) Run this app
**3.1 If you forgot the master password reset this**
4) Create server with same port used by your postgreSQL server.

### Install pgmodeler

1) Open your terminal
```bash
git clone https://github.com/pgmodeler/pgmodeler.git
cd pgmodeler
git checkout master
```
2) Check if you have installed postgresql
```bash
postgres -V
```
3) Open and edit **pgmodeler.pri** *(
Warning Please, the routes and version are not necessarily the same as me)*
```shell
macx {
  !defined(PGSQL_LIB, var): PGSQL_LIB = /Applications/Postgres.app/Contents/Versions/13/lib/libpq.dylib
  !defined(PGSQL_INC, var): PGSQL_INC = /Applications/Postgres.app/Contents/Versions/13/include
  !defined(XML_INC, var): XML_INC = /Applications/Xcode.app/Contents/Developer/Platforms/MacOSX.platform/Developer/SDKs/MacOSX.sdk/usr/include/libxml2
  !defined(XML_LIB, var): XML_LIB = /usr/lib/libxml2.dylib
  INCLUDEPATH += $$PGSQL_INC $$XML_INC
}
```
4) Install dependencies with brew
```bash
brew install qt libxml2 libpq
```
5) Build the app
```bash
qmake -r pgmodeler.pro
make && make install
```

pgmodeler is now available in your applications