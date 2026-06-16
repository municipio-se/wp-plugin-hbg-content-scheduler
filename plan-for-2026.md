# Plan for LTS 2026

Bas: `3.1.3`. Nuvarande LTS-head: `5b8ba98`. Ny upstream-bas: `3.1.8`.

## Slutsats

Upstream `3.1.8` är en rimlig ny bas, men LTS-forkens cron-/hook-beteende runt
avpublicering behöver porteras eller verifieras innan release.

## Arbetsplan

- [ ] Starta från upstream `3.1.8`.
- [ ] Återskapa Composer- och installer-metadata för LTS.
- [ ] Skriv om LTS cron-fixen ovanpå upstreams nuvarande `Unpublish`-klass.
- [ ] Behåll upstreams offset-baserade timestamp-lösning om den fungerar med
      WordPress tidszoninställning.
- [ ] Verifiera schemaläggning, omschemaläggning och borttagning av gamla
      cron-events.
- [ ] Verifiera autoload-strategin mot LTS-metapaketet.

## Beslutstabell

| Område | Vår slutändring | Upstream-läge | Bedömning | Berörda commits |
| --- | --- | --- | --- | --- |
| Composer och paketering | Bytte till `municipio/wp-plugin-hbg-content-scheduler`, GPL, installer-konfiguration och root-vendor-antagande. | Upstream är kvar på `helsingborg-stad/content-scheduler`, MIT och inkluderar plugin-lokal autoload. | Återskapa smalare | `bfe7b2a`, `8970112`, `7444a42` |
| Unpublish hook och cron-args | Accepterar två hook-argument och schemalägger med numeriska cron-args. | Upstream använder associativa args, men hook-registreringen behöver särskild kontroll så åtgärden inte tappas. | Återskapa smalare | `abafc58`, `ecb433b` |
| Tidszon/timestamp | Hårdkodade `Europe/Stockholm` för timestamp. | Upstream har offset-baserad timestamp-hantering. | Ersätt | `472d667`, `80585d3` |
| CSS/cache busting | Pekade cache bust mot CSS i stället för SCSS. | Patchen motsvaras av upstreamändring. | Släpp | `82ed76a` |
| Fataler vid postskapande | LTS rättade fataler kopplade till skapande/autoload-flöde. | Upstream har annan vendor/autoload-yta. | Verifiera manuellt | `fb1c377`, `905b9c1` |
| Dokumentation/licens/release | LTS-specifik dokumentation och metadata. | Ska skrivas om efter faktisk rebase. | Ej relevant | README-/licenscommits |

## Risker att verifiera

- `unpublish_post` måste föra med korrekt action (`draft`/`trash`) hela vägen
  till schemalagd event.
- Autoload-strategin måste matcha LTS-metapaketet.
- Manuell funktionstest behövs för både schemaläggning och borttagning av gamla
  cron-events.

## Analyskommandon

- `git diff --stat 3.1.3..HEAD`
- `git diff --stat 3.1.3..3.1.8`
- `git diff --stat HEAD..3.1.8`
- `git log --reverse --format='%h%x09%ad%x09%s' --date=short 3.1.3..HEAD`
- `git log --reverse --format='%h%x09%ad%x09%s' --date=short 3.1.3..3.1.8`
- Riktade `git diff`, `git show`, `git grep` och `git cherry` för Composer,
  bootstrap, `App.php` och `Unpublish.php`.
