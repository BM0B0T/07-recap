# PGR301 Flow recap 

I denne øvingen skal dere jobbe selvstendig med det vi har lært i PGR301 så langt. Hensikten er at dere, uten instruksjoner, skal være i stand til å lage et utviklingsmiljø som tilfredstiller gode DevOps prinsipper for flyt uten detaljerte instruksjoner. 
Dere står fritt til å improvisere denne øvingen og gjøre ting i den rekkefølgen dere vil men her er et forslag ; 

* Et Cloud9 miljø er laget for dere som "vanlig" https://244530008913.signin.aws.amazon.com/console
 * Et ECR repository er laget for dere som heter "studentnavn"-private

Resten må klare selv, lykke til!

## Spring Boot eksempel app

* Lag et nytt GitHub repository med en ny Spring Boot applikasjon https://start.spring.io/ - og lag en spring boot applikasjon som eksponerer et REST grensesnitt.
* For inspirasjon se gjerne her 

Relevant info 

* https://github.com/glennbechdevops/spring-docker-dockerhub
* https://medium.com/nerd-for-tech/building-a-simple-restful-api-with-spring-boot-2351687ecab0

## Branch protection

* Sett opp _main_ branch som en beskyttet branch, slik at ingen kan comitte direkte men kun via pull request. 
* Legg til en medstudent som collaborator på ditt repository og lag en regel som sier at en pull request trenger minst en godkjenning før den kan merges. 
* For å enklere kunne jobbe, kan dere godt fjerne denne reglen før dere går videre. 

Relevant info 

https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/about-protected-branches

## Github Actions
 
* Lag en GitHub Actions workflow som kompilerer, tester og bygger Spring boot applikasjonen din på hver commit til main
* Lag en ny regel på den beskyttede main branchen som gjør at vi ikke kan merge en pull request før vi har minst et vellykket bygg.* 

Relevant info 

* https://github.com/glennbechdevops/01-CI-Github-actions
* https://docs.github.com/en/actions

## Cloud 9

* Logg inn på Cloud 9 miljøet ditt 
* Lag en klone av ditt nye repository i cloud 9  

## AWS Lamba og SAM

* Fra terminaleni i Cloud9, gjør en ```sam init``` og lag et nytt SAM prosjekt for Javascript eller Python
* Se på koden som blir laget, og test ut ```sam build --use-container``` osv
* Det er ikke viktig å lage en github actions forkflow for SAM, vi øver det samme prinsippet med Docker/Java senere.

Relevant info

* https://github.com/glennbechdevops/02-lambda-sls-cd-only (Vi lagde aldri et prosjekt fra scratch i denne labben - så dette er en ekstra challenge)

## Hemmeligheter

* Finn AWS brukeren din og lag access keys
* Konfigurer GitHub repositoryet ditt med repository secrets, slik at cloud 9 får tilgang til AWS som din bruker 

Relevant info

* https://github.com/glennbechdevops/02-CD-AWS-lamda-sls
* https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html

## Docker

* Lag en Dockerfile slik at du kan pakke spring boot applikasjonen din som et Docker image. 
* Lag et "multi stage" docker" build
* Kjør applikasjonen din i Cloud 9, fra en terminal, både som Docker container og ved hjelp av Maven

Relevant info 

* https://github.com/glennbechdevops/spring-docker-dockerhub
* https://docs.docker.com/build/building/multi-stage/

## Docker ECR og Docker Hub 

* Sjekk at du har konto på Dockerhub 
* Prøv å pusher docker images dit fra Cloud 9 til Dockerhub 
* Et ECR repository i AWS kontoen vi bruker er laget for dere som heter <studentnavn>-private.
* Se at du kan pushe et docker image til dette ECR repositoryet . 

## Docker i GitHub actions 

* Se at du kan lage en GitHub actions workflow som bygger et container image  og pusher til ECR

Relevant info

* https://github.com/glennbechdevops/spring-docker-dockerhub






