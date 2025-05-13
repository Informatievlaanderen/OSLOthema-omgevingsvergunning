# Omgevingsinformatie linken met Besluit
Leveranciers van omgevingsvergunningsdossier-software gaan volgens deze OSLO standaard informatie ontsluiten. 
Daarbij is het belangrijk dat ook de besluitinformatie mee opgenomen wordt die relevant is.

Deze pagina legt uit hoe de link tussen omgevingsinformatie (rechtshandelingen, inhoud...) en besluiten gelegd kunnen worden.

# Tijdens het notuleren

Tijdens het notuleren worden er eerst notities genomen in een document.
Dit document kan gemapt worden op [Representatie](https://data.vlaanderen.be/doc/applicatieprofiel/dossier/#Representatie) of Item (FRBR model).
Dit is nog geen [Besluit](https://data.vlaanderen.be/ns/besluit/#Besluit), dat een expressie (FRBR model) is.

Het document wordt gelinkt met de Rechtshandeling via volgende eigenschap:
- [document](https://data.vlaanderen.be/ns/omgevingsvergunning#document)

Voorbeeld van een Aanvraag (Rechtshandeling) en een document:

```
@prefix omgevingsvergunning: <https://data.vlaanderen.be/ns/omgevingsvergunning#> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

<https://data.vlaanderen.be/id/omv/aan/1> a omgevingsvergunning:Aanvraag ;
    omgevingsvergunning:aanvrager <https://data.vlaanderen.be/id/org/regorg/1> ;
    omgevingsvergunning:inhoud <https://data.vlaanderen.be/id/omv/bep/1> ;  
    omgevingsvergunning:document <https://data.vlaanderen.be/doc/1> .

<https://data.vlaanderen.be/doc/1> a foaf:Document .
```

# Na beslissing

Pas na de beslissing wordt het besluit, dat ook een document is, opgemaakt en kan er dus gelinkt worden met [Besluit](https://data.vlaanderen.be/ns/besluit/#Besluit).

Het besluit wordt gelinkt met Juridisch Werk via volgende eigenschap:
- [realiseert](http://data.europa.eu/eli/ontology#realizes)

Er kan met zowel Rechtshandelingen als Inhoud gelinkt worden, gezien beide specialisaties van Juridisch Werk zijn.

In het voorbeeld hieronder leggen we de relatie tussen Besluit en Aanvraag (Rechtshandeling), als ook een relatie tussen Artikel, wat een onderdeel is van een Besluit, en de Inhoud.

```
@prefix omgevingsvergunning: <https://data.vlaanderen.be/ns/omgevingsvergunning#> .
@prefix foaf: <http://xmlns.com/foaf/0.1/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .
@prefix besluit: <http://data.vlaanderen.be/ns/besluit#> .
@prefix eli: <http://data.europa.eu/eli/ontology#> .

<https://data.vlaanderen.be/id/omv/aan/1> a omgevingsvergunning:Aanvraag ;
    omgevingsvergunning:aanvrager <https://data.vlaanderen.be/id/org/regorg/1> ;
    omgevingsvergunning:inhoud <https://data.vlaanderen.be/id/omv/bep/1> ;
    omgevingsvergunning:document <https://data.vlaanderen.be/doc/1> .

<https://data.vlaanderen.be/doc/1> a foaf:Document .

<https://data.vlaanderen.be/id/besluit/1> a besluit:Besluit ;
    eli:realizes <https://data.vlaanderen.be/id/omv/aan/1> ;
    eli:has_part <https://data.vlaanderen.be/id/besluit/1/artikel/2> .


<https://data.vlaanderen.be/id/besluit/1/artikel/2> a besluit:Artikel ;
    eli:realizes <https://data.vlaanderen.be/id/omv/bep/1> .
```


