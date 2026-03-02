---
title: Annexes
description: Annexes du stage Diluz

# date: 2022-06-09T20:12:52+08:00
# lastmod: 2022-06-09T20:12:52+08:00
---

## Files

>Mettre les annexes ici



## Exemple de code mis en place dans le back-end de l'application :
```ts
/**
 * Convertit une chaîne de caractères au format JSON en objet JavaScript.
 * @param parameter - Chaîne JSON à parser. Peut être undefined.
 * @returns L'objet JavaScript issu du parsing JSON, ou undefined si le paramètre est absent.
 */
parserOfObjects(parameter: string | undefined){
    if (parameter !== undefined) {
        const res = JSON.parse(parameter);
        return res;
    }
};

// Vérifie si un saut de page est nécessaire et ajoute une nouvelle page si besoin.
checkPageBreak(pdf: jsPDF, yPosition: number, lineHeight = 6): number {
    const pageHeight = pdf.internal.pageSize.getHeight();
    const marginBottom = 15;
    if (yPosition + lineHeight > pageHeight - marginBottom) {
        pdf.addPage();
        return 20; // position Y de départ sur la nouvelle page
    }
    return yPosition;
}

const val = this.parserOfObjects(part3.distributionPartners); // converti les données pour les exploiter
const arrayDistriPartners: string[] = [];
yPosition = this.checkPageBreak(pdf, yPosition); // vérifie si fin de page ou pas, saute une ligne si oui
pdf.text(`Nombre d'associé(s) soumis au régime TNS : ${val.length}`, xPosition + 20, yPosition); // nombre d'associé(s)
yPosition += 6;
val.forEach((v: any, index: number) => {
    arrayDistriPartners.push(
        `Associé n°${index + 1} :`,
        `   Nom et Prénom : ${v.fullname}`,
        `   Solde moyen annuel du compte courant associé : ${v.currentAccount} `,
    );
});
arrayDistriPartners.forEach(line => { // pour chaque objet json,
    yPosition = this.checkPageBreak(pdf, yPosition); // vérifier la fin de page et sauter si besoin
    pdf.text(line, xPosition + 25, yPosition); // afficher en texte les lignes
    yPosition += 6; // saut de ligne pour éviter les textes d'être superposés
});
```
> Les 2 fonctions au dessus sont utilisés presque partout afin de permettre une meilleure structure du PDF ainsi que de pouvoir utiliser les données mises sous forme d'objet.
>
> Ce formulaire, structuré en trois grandes parties, et ses données ont été retransférées dans le PDF désignant le client X ou Y.

> Quand aux 2 dernières semaine de ce stage, il a été convié de merger ma branch (de GitLab) sur la branch Develop afin de donner l'accès aux pôle juridique de pouvoir tester mon travail, renvoyer des choses à améliorer / à changer, puis permettre la sauvegarde du PDF dans la base de données, et de télécharger ce dernier directement dans le Navigateur.
