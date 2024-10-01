# Merge vs rebase

Wanneer je met meerdere personen samenwerkt aan dezelfde codebase, zul je de wijzigingen van anderen moeten integreren in je eigen werk. Meestal worden hiervoor zogenaamde "merge commits" gebruikt. Het probleem hiermee is dat hierdoor de historiek van de repository dan al snel ingewikkeld wordt. Een alternatief is om de wijzigingen van anderen te "rebasen" op jouw werk. Dit zorgt voor een veel eenvoudigere historiek, maar vraagt een zekere discipline.

Hieronder tonen we het verschil en hoe je een *rebase* uitvoert.

## Merge

Stel, Alice en Bob werken samen aan een project, en hebben elk een kloon gemaakt van de branch `main` op de Github-repository van hun team.

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
```

De commit-id's kan je als volgt interpreteren: `m1` en `m2` duiden de volgorde aan van deze commits op de `main` branch. De hexadecimale string stelt de hash voor van deze commit. Hieronder duiden we de commits van Alice aan met `a1` en `a2`, en die van Bob met `b1` en `b2`, eveneens gevolgd door een (fictieve) hash.

Alice heeft lokaal enkele nieuwe commits gemaakt. Zowel Alice als Bob werken gewoon op de `main` branch, dus aparte branches nemen we hier zelfs niet in rekening.

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
    branch alice
        commit id: "a1-0bad10f"
        commit id: "a2-3b1b3f4"
```

Intussen is ook Bob wijzigingen aan het maken:

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
    branch bob
        commit id: "b1-84ea106"
        commit id: "b2-a8ba556"
```

Alice is de eerste die naar Git gepushed heeft, dus voor Bob is de situatie nu als volgt:

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
    branch bob
        commit id: "b1-84ea106"
        commit id: "b2-a8ba556"
    checkout main
    commit id: "a1-0bad10f"
    commit id: "a2-3b1b3f4"
```

Als Bob een push naar Github wil doen, zal deze uiteraard geweigerd worden. Hij moet eerst de commits van Alice integreren in zijn lokale kopie. Bij een `git pull` zal Git een merge commit maken, d.w.z. een commit die de wijzigingen van Alice en Bob samenbrengt:

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
    branch bob
        commit id: "b1-84ea106"
        commit id: "b2-a8ba556"
    checkout main
    commit id: "a1-0bad10f"
    commit id: "a2-3b1b3f4"
    checkout bob
    merge main id: "b3-0bad108"
```

Na het eventueel oplossen van merge-conflicten kan Bob nu zijn werk naar Github pushen, maar de historiek is nu wel wat ingewikkeld. Wanneer je ook met meerdere mensen samenwerkt (die bv. ook nog eens andere combinaties van commits moeten mergen), kan dit al snel onoverzichtelijk worden.

## Rebase

Een alternatief is dat Bob eerst de commits van Alice binnen haalt, en dan zijn eigen commits achteraan in de historiek toevoegt. Dit heet een *rebase*.

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
    commit id: "a1-0bad10f"
    commit id: "a2-3b1b3f4"
    branch bob
        commit id: "b1-b47ca47"
        commit id: "b2-a1069a3"
```

Merk op dat de commit hashes van Bob nu veranderd zijn omdat de commits van Alice er nu voor staan. Dit is normaal bij een rebase. Bob kan nu zijn werk naar Github pushen, en de historiek is veel eenvoudiger:

```mermaid
gitGraph
    commit id: "m1-c055049"
    commit id: "m2-7b1b3f4"
    commit id: "a1-0bad10f"
    commit id: "a2-3b1b3f4"
    commit id: "b1-b47ca47"
    commit id: "b2-a1069a3"
```

Als elk teamlid deze manier van werken aanhoudt, blijft de historiek een stuk eenvoudiger om over te redeneren. Het principe is dus dat je de bestaande historiek niet wijzigt, en je eigen commits altijd achteraan toevoegt.

## Aanbeveling

Telkens wanneer je een `git pull` uitvoert, is het best dat je de optie `--rebase` meegeeft. Dit zorgt ervoor dat Git automatisch een rebase uitvoert in plaats van een merge.

Je kan Git zo instellen dat wanneer je een `git pull` uitvoert, Git automatisch een rebase doet in plaats van een merge. Dit doe je met de volgende commando's:

```console
> git config --global pull.rebase true
> git config --global rebase.autoStash true
```

De eerste regel zorgt ervoor dat Git standaard een rebase doet bij een pull, de tweede regel zorgt ervoor dat Git automatisch je eventuele lokale wijzigingen opzij zet en terug toepast na de rebase.
