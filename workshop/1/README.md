## Oppgave 1
 
* Bli invitert inn i motoren-site gruppa.

* I motoren-site gruppa ligger det deploy-key til Digital Ocean K8s cluster som en secret. Dvs. det er mulig å lese verdien av denne hemmligheten i en github action på følgande måte: 
```
${{ secrets.DIGITAL_OCEAN_TOKEN }}
```

* Opprett repo under motoren-site, lag en hello world app (valgfri teknologi/smak), bygg det med docker, push det til docker repo: (registry.digitalocean.com/containers). 
Sjå [.github/workflows/main.yml](.github/workflows/main.yml) og https://github.com/motoren-site/github-actions for hjelp.
