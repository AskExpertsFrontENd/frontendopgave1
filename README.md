Vores korte reflektion:

Hvis vi ser tilbage på vores opgave som vi nu har færdigudviklet, har vi set en masse udfordringer samt successer i processen. Hvis vi kigger først på vores successer synes vi at der ikke var meget javascript, men næsten kun html og css, dog skulle man benytte sig af nye css-sætninger som gjorde det hele en smule usikkert at sidde i. F.eks alt det med child selectors. Løbende har vi fundet ud af at implementere det, dog har vi haft svært ved det. Samtidig har vi også haft svært ved at kunne finde rundt i dokumentet til at starte med, da noget allerede var oprettet og sat ind, men ikke stylet. og andet var der ikke, samtdig manglede nogle billeder og andre billeder var der, og det så meget rodet ud til at starte med.

Hvis vi tager et eksempel fra vores kodning i skolen og ser hvordan vi har implementeret det i vores opgave, har vi et her:

.employees-grid {
display: grid;
grid-template-columns: repeat(3, minmax(280px, 1fr));
gap: 3rem 2rem;
justify-content: center;
grid-auto-rows: auto;
}

@supports (grid-template-rows: subgrid) {
.employees-grid {

      grid-template-rows: auto 1fr auto;
    }

}
@supports not (grid-template-rows: subgrid) {
.employees-grid {
grid-auto-rows: auto;
}
}

I denne kode bruges CSS Grid som standardløsning til at vise medarbejderkort i et responsivt layout med tre kolonner. Der er derefter lavet en fallback-struktur med @supports, hvor browseren først bruger den normale grid-løsning, og kun hvis subgrid understøttes, aktiveres en mere avanceret rækkestruktur med grid-template-rows: auto 1fr auto. Det betyder, at layoutet kan blive mere ensartet i moderne browsere, mens ældre browsere stadig viser indholdet korrekt. @supports not (...) fungerer som en eksplicit fallback, så designet forbliver stabilt og brugbart, selv hvis browseren ikke understøtter subgrid. På den måde er løsningen bygget efter princippet om progressive enhancement, hvor alle får en fungerende version, og nyere browsere får en forbedret oplevelse.
samtidig bruger vi defensive css i dette omfang, så at vores kodning ikke "falder fra hinanden"
