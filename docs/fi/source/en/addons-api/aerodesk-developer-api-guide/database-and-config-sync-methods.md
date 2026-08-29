# Tietokannan & Konfiguraation Synkronointimenetelmät

Hallitse aktiivista tietokantayhteyttä ja synkronoi konfiguraation muutokset koko järjestelmässä välittömästi. Muista tallentaa config kun olet tehnyt suoria muutoksia API:n kautta.

- Tarkista aktiivinen DB: `getApi().getBotConfig().database.activeDatabase;` _(Palauttaa "MySQL", "SQLite", "MongoDB", jne.)_
- Hae DB Host: `getApi().getBotConfig().database.host;`
- Tallenna Config Muutokset: `getApi().saveConfig();` __(Takaa kaikki API:n kautta tehdyt muokkaukset tallennetaan tietokantaan/YAML)_
- Lataa konfigurointi: `getApi().reloadConfig();` _(Pakottaa botin vetämään tuoreita tietoja tietokannasta)_
