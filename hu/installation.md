# Telepítés

- [Telepítés](#installation)
    - [Rendszerkövetelmények](#server-requirements)
    - [Laravel telepítése](#installing-laravel)
    - [Konfiguráció](#configuration)

<a name="installation"></a>
## Telepítés

<a name="server-requirements"></a>
### Rendszerkövetelmények

A Laravel keretrendszerhez használatához szükséges néhány követelmény. Természetesen a [Laravel Homestead](/docs/{{version}}/homestead) virtuális gép az összes követelménynek megfelel, szóval erősen javallott a Homestead használata lokális fejlesztési környezetként.

Ha nem használod a Homesteadet, a következő elvárásoknak kell megfelelnie a szerverednek:

<div class="content-list" markdown="1">
- PHP >= 5.6.4
- OpenSSL PHP Extension
- PDO PHP Extension
- Mbstring PHP Extension
- Tokenizer PHP Extension
</div>

<a name="installing-laravel"></a>
### A Laravel telepítése

A Laravel a [Composer](http://getcomposer.org) csomagkezelőt használja a függőségek kezelésére. Mielött használnád a Laravelt, ellenőrizd, hogy a Composer telepítve van-e a számítógépeden.

#### Laravel Installer-en keresztül

Előszőr is töltsd le a Laravel Installert a Composer használatával:

    composer global require "laravel/installer"

Ellenőrizd, hogy a  `~/.composer/vendor/bin` mappa (vagy az ennek megfelelő mappa a te OS-eden) hozzá van adva a $PATH-hoz, magyarán a rendszered megtalálja-e a `laravel` futtatható álományát.

Telepítás után a `laravel new` parancs létrehoz egy friss Laravel telepítést az általad megadott mappába. Például a `laravel new blog` készít egy új blog mappát, ami tartalmazza a friss Laravel telepítést és az összes függőségét:

    laravel new blog

#### Composer Create-Project-en keresztül

Alternatívaként telepítheted a Laravelt a Composer `create-project` használatával a terminálon keresztül:

    composer create-project --prefer-dist laravel/laravel blog

#### Helyi fejlesztői szerver:

Ha van helyileg PHP telepítve és szeretnéd, hogy a PHP-ba épített fejlsztői szerver szolgálja ki az applikációdat, akkor a `serve` Artisan parancsot használd. Ez a parancs elindítja a feljesztői szervert a `http://localhost:8000` címen:

    php artisan serve

Természetesen sokkal teljeskörübb fejlesztői lehetetőségek érhetők el a [Homestead](/docs/{{version}}/homestead) és a [Valet](/docs/{{version}}/valet) által.

<a name="configuration"></a>
### Konfiguráció

#### Public Könyvtár

A Laravel telepítése után valószínüleg be kell állítanod, hogy  a webszervered document / web root könyvtára a `public` mappa legyen. Az abban a könyvtárban található `index.php` szolgál legelső controllerként, és ez felel az összes HTTP kérés belépőpontként a programodba.

#### Konfigurációs fájlok

Minden konfigurációs fájl ami szükséges a Laravel keretrendszerhez a `config` mappában található. Minden konfigurációs fájlt jól dokumentált, érdemes áttekinteni minden beállítási módot ami rendelkezésedre áll.

#### Könyvár jogosultságok

A Laravel telepítése után valószínüleg be kell állítanod pár jogosultságot. A `storage` és a `bootstrap/cache` könyvtáraknak írhatónak kell lennie a web szerver által, külömben a a Laravel nem fog futni. Ha [Homestead](/docs/{{version}}/homestead) virtuális gépet használsz, ezek a jogosultságok előre be vannak állítva.

#### Applikáció Kulcs

A következő dolog, amit meg kell tenned a Laravel telepítése után, hogy beállítasz egy random stringet applikációs kulcsként. Ha a Laravelt a Composeren vagy a Laravel installeren kereszül telepítetted akkor a telepítő ezt megtette neked a  `php artisan key:generate` parancs automatikus futtatásával.

Általánosságban a kulcsnak 32 karakter hosszúnak kell lennie.  A kulcs a `.env` futtató környezeti fájlban állítható be. Ha még nem nevezted át a `.env.example` fájlt `.env`-re, akkor most kellene megtenned. **Ha az applikációs kulcs nincs beállítva, a felhasználó sessionök és az egyéb titkosított adataid nem lesznek biztonságosan!**

#### További konfigurációs lehetőségek

A Laravelnek általában nincs szüksége az alapértelmezetteken kívül további beállításokra. Már kezdheted is a fejlesztést! Mindenesetre érdemes áttekinteni a `config/app.php` fájlt, amelyben minden beállítási lehetőség dokumentálva van. Tartalmaz például `timezone`(időzona) és `locale`(nyelv) beállításokat, amiket valószínűleg módosítani szeretnél, hogy megfelelő legyen az alkalmazásodhoz.

Valószínüleg a Laravel egyéb komponenseit is szeretnéd konfigurálni, mint például:

<div class="content-list" markdown="1">
- [Cache](/docs/{{version}}/cache#configuration)
- [Adatbázis](/docs/{{version}}/database#configuration)
- [Session](/docs/{{version}}/session#configuration)
</div>

Ha a Laravel már telepítve van, érdemes a [helyi fejlesztői környezetet is beállítani](/docs/{{version}}/configuration#environment-configuration).
