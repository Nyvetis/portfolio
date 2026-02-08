---
date: 2026-01-12
description: "Work in progress..."
image: '/image/Galaxy.webp'
lastmod: 2026-01-13
showTableOfContents: true
categories: [ "formation", "stage"]
tags: ["JS", "VueJS","NodeJS", "TypeScript", "Docker"]
title: "Stage Diluz"
cover: '/image/Galaxy.webp'
type: "post"
--- 
# Diluz

> Diluz est une entreprise ratachée au groupe Talenz, et plus patriculièrement dans le cas de Chantepie, à Talenz Toadenn.
> Talenz qui est un groupe d'expertise comptable.
>
> Ce stage à été obtenu via l'offre de stage reçu à mon lycée, qui m'a été transmise afin de postuler à ce stage, qui suite à un entretien avec le maître de stage, permettant de mettre en point les différentes missions et tâches à accomplir, une réponse favorable pour être pris en tant que stagiaire du `12 Janvier au 20 Février 2026`.
>
> Le but de ce stage est de découvrir le monde de l'entreprise, et plus particulièrement les différents environnements de travail possible afin de me préparer plus tard au métier de développeur (full stack & devops dans ce cas ci), ainsi que de renforcer mes compétences, dont certaines nécéssaires à l'obtention de mon BTS SIO.
>
> Les missions qui m'ont été affecté pour l'instant est de :
> - Mises à jour des fichiers de configuration docker (code legacy)
> - Mise en création d'un bouton permettant l'enregistrement sous forme de PDF, une annexe juridique sous forme de formulaire afin de répondre au besoin du pôle juridique de Talenz Toadenn, étant d'avoir un bouton pouvant exporter en PDF cette dite annexe juridique au lieu de devoir recopier les données à la main sur un document Word à coté.
> - Dans le back-end, réalisé via le langage `TypeScript` et sa librairie `jsPDF` et `jsPDF-autotable`, et ensuite déposer le pdf dans la base de données, pour le télécharger via le navigateur (car impossible directement via le back-end).

> Lors des premières semaines, le but était de réussir à mettre en place le poste de travail, ainsi que les environnements de travail et projets, afin de pouvoir réussir à programmer de façon à ne pas le faire à l'aveugle (comme mis dans les Comptes Rendus D'activité, certains jours ont été de la programmation à l'aveugle dû au fait de ne pas avoir l'environnement de prêt et donc l'accès au front et aux données).

> Une fois l'environnement enfin mis en place, j'ai pu commmencer bien efficacement à récupérer les bons attributs des tables et bases de données en fonction de de la structure du formulaire d'annexe juridique.

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
