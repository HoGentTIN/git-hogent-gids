# Wijzigingen binnenhalen

Als je een repository hebt gecloned, is dat maar een simpele **kopie** van de repository op dat moment. Jouw lokale kopie is wel gelinkt aan de originele repository via een zogenaamde remote.

Je kan de remote van je repository bekijken met het commando `git remote -v`. Dit toont je de URL van de remote repository.

Als er wijzigingen zijn in de originele repository, moet je die zelf binnenhalen. Dit kan op twee manieren: `git fetch` en `git pull`. Beide halen wijzigingen op van een externe repository, maar ze doen dat op een andere manier.

## `git fetch`

Het `git fetch` commando haalt wijzigingen op van een externe repository, zoals GitHub, maar voert deze niet automatisch samen met je lokale code. Dit betekent dat de wijzigingen van de externe repository alleen worden opgehaald en naar een lokale referentie worden gebracht. Je lokale repository is dus wel op de hoogte van de wijzigingen maar ze zijn niet uitgevoerd.

Na het uitvoeren van `git fetch` kan je bekijken wat het volgende uit te voeren commando is via `git status`. Dit commando is je beste vriend en zal altijd helpen om te zien wat er moet gebeuren.

## `git pull`

Het `git pull` commando haalt ook wijzigingen op van een externe repository, maar voert deze wel automatisch samen met je lokale code.

Dit kan ervoor zorgen dat je conflicten krijgt als er wijzigingen zijn in de externe repository die niet compatibel zijn met jouw lokale wijzigingen. Daarom is het veiliger om `git pull --rebase` te gebruiken, wat dit precies doet, lees je in de [merge vs rebase](./merge-rebase.md) sectie.

## Samenvatting

Het is altijd beter om eerst `git fetch` uit te voeren en te bekijken wat er veranderd is, via bv. `git status`. Daarna kan je eventueel `git pull` doen om de wijzigingen samen te voegen met je lokale code.
