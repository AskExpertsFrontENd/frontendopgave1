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

Som nævnt for oven er progressive enhancement brugt flere steder i løsningen. Et tydeligt eksempel er vores FAQ sektion, hvor vi bruger native HTML elementer.

<details>
  <summary>Her er spørgsmåles</summary>
  <p>og svaret</p>
</details>

Her virker funktionaliteten helt uden JavaScript. Derudover har vi tilføjet animation via CSS, som kun anvendes i browsere, der understøtter det. Vi har også taget hensyn til brugere med reduceret bevægelse.

@media (prefers-reduced-motion: reduce) {
  .about-faq__content {
    transition: none;
  }
}

Dette sikrer en tilgængelig løsning.

Vi har organiseret vores CSS med en kombination af globale styles og komponent specifik CSS. Global CSS bruges til tokens (farver, spacing og typografi), som er defineret i tokens.css. Den komponent specifike CSS ligger direkte i hver .astro komponent, hvilket gør det lettere at isolere og vedligeholde styles. Vi har også arbejdet med custom properties/tokens enkelte steder, som gør det nemmere at genbruge værdier og sikre konsistens i designet.

Som nævnt før fik @supports os til at indse vigtigheden i defensive css, hvilket også kan ses i denne relative color sytax, hvor knapper/links på hover eller aktiv state får et farveskifte, dog kun på enheder der acceptere dette. 

@supports (color: oklch(from red l c h)) {
  .button:hover {
    background: oklch(from var(--color-ui-primary) calc(l - 0.08) c h);
  }
}


Konklusion:

Overordnet har opgaven givet os en bedre forståelse for, hvordan man omsætter et figma design til en vedligeholdelsesvenlig og fungerbar løsning. Vi har især arbejdet med moderne CSS teknikker og fået erfaring med defensive CSS og progressive enhancement, som har gjort vores løsning mere stærk. Derudover har vi opnået en bredere forståelse for strukturering af komponenter, samt genbrug af styles gennem tokens. 