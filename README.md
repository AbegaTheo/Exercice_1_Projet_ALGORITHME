# Exercice_1_Projet_ALGORITHME

README.md

LECTURE DE CARACTERE DE PHRASE

Ce programme écrit en pseudo-code est conçu pour analyser une phrase saisie par l'utilisateur. L'objectif est de déterminer la longueur de la phrase, le nombre de mots et le nombre de voyelles dans la phrase. La phrase saisie doit se terminer par un point (".").

Objectifs

L'algorithme répond aux objectifs suivants :

1. Calculer la longueur de la phrase, sans inclure le point final.


2. Compter le nombre de mots, en supposant que les mots sont séparés par des espaces.


3. Compter le nombre de voyelles dans la phrase (les voyelles considérées sont a, e, i, o, u, y en minuscules et A, E, I, O, U, Y en majuscules).


4. Gérer correctement les espaces pour compter les mots et ignorer les espaces en excès.



Fonctionnement du Programme

Le programme effectue les étapes suivantes :

1. Demande à l'utilisateur de saisir une phrase terminée par un point.


2. L'algorithme parcourt chaque caractère de la phrase :

Compte la longueur de la phrase (en excluant le point final).

Compte le nombre de voyelles dans la phrase.

Compte le nombre de mots, en détectant les espaces qui séparent les mots.


3. Affiche le résultat final : la longueur de la phrase, le nombre de mots et le nombre de voyelles.



Programme pseudo-code


ALGORITHM LECTURE_DE_CARACTERE_DE_PHRASE
VAR
   // Déclaration des variables
   longueur_de_la_phrase : INTEGER;
   nombre_de_mots : INTEGER;
   nombre_de_voyelle : INTEGER;
   phrase : STRING;
   voyelles : STRING;
   n, i : INTEGER;
   caractere : CHAR;
   dernierEstEspace, fin_de_phrase : BOOLEAN;

BEGIN

   // Initialisation des variables
   longueur_de_phrase := 0;  // Compteur pour la longueur de la phrase
   nombre_de_mots := 0;     // Compteur pour le nombre de mots
   nombre_de_voyelle := 0;  // Compteur pour le nombre de voyelles
   voyelles := "aeiouyAEIOUY";  // Liste des voyelles (majuscules et minuscules)
   dernierEstEspace := true;  // Indicateur pour savoir si le dernier caractère était un espace
   fin_de_phrase := false;   // Variable pour contrôler la fin de la phrase (point final)

   // Lecture de la phrase de l'utilisateur
   Writeln("Entrez une phrase terminée par un point : ");
   Read(phrase);   // Lire la phrase de l'utilisateur

   // Calculer la taille de la phrase sans compter le point final
   n := phrase.length - 1;  // la variable recoit la taille de la phrase sans le point final

   //Parcourir chaque caractère de la phrase
   FOR i FROM 0 TO n-1  DO
      caractere := phrase[i]   // Recupere le caractère actuel

      // Verifie si le caractère est un point (fin de la phrase)
      IF (caractere == '.') THEN
         fin_de_phrase = true;  // Il marque la fin de la phrase et sort de la boucle
      END_IF

      // Si caractere n'est pas un point, on continue les traitements
      IF (fin_de_phrase == false) THEN
         //Incrementation de la longueur de la phrase
         longueur_de_phrase := longueur_de_phrase + 1;
         
         // vérification si le caractère est une voyelle
         IF (caractere = 'a' || caractere = 'e' || caractere = 'i' || caractere = 'o' || caractere = 'u' || caractere = 'y' `\n
               || caractere = 'A' || caractere = 'E' || caractere = 'I' || caractere = 'O' || caractere = 'U' || caractere = 'Y') THEN
            nombre_de_voyelle := nombre_de_voyelle + 1   // Incrémenter le compteur de voyelles
         END_IF

         // Détecter les mots dans la phrase
         IF caractere <> ' ' THEN   // Si le caractère n'est pas un espace
            IF dernierEstEspace THEN
               nombre_de_mots := nombre_de_mots + 1 // Compter un nouveau mot
            END_IF
            dernierEstEspace := false  // Le caractère actuel n'est pas un espace
         ELSE
            dernierEstEspace := true // L'espace est rencontré, le prochain mot commenece après cet espace
         END_IF
      END_IF
   END_FOR

   // Affichage des résultats
   Writeln("Longueur de la phrase : ", longueur_de_la_phrase)
   Writeln("Nombre de mots dans la phrase : ", nombre_de_mots)
   Writeln("Nombre de voyelles dans la phrase : ", nombre_de_voyelle)

END



Exemples de sortie :

1. Entrée : "salut tout le monde."

Sortie attendue :

Longueur de la phrase : 19
Nombre de mots dans la phrase : 4
Nombre de voyelles dans la phrase : 7