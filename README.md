import random

 # Fonction pour choisir un mot au hasard dans une liste
def choisir_mot():
    mots = ["python", "ordinateur", "jeu", "programmation", "intelligence", "soleil", "lune", "arbre", "amour", "bonheur", "musique", "voyage", "etoile", "ocean", "mystere"]
    return random.choice(mots)

# Fonction pour afficher le mot avec des lettres cachées (_)
def afficher_mot_cache(mot, lettres_trouvees):
    return " ".join([lettre if lettre in lettres_trouvees else "_" for lettre in mot])

# Fonction principale du jeu
def jeu_devine_mot():
    mot_a_trouver = choisir_mot() # Mot à deviner
    lettres_trouvees = set() # Ensemble des lettres déjà devinées
    tentatives = 10

    print("Bienvenue dans le jeu de devinette de mots !")

    while tentatives > 0:
        print("\nMot à deviner :", afficher_mot_cache(mot_a_trouver, lettres_trouvees))
        lettre = input("Proposez une lettre : ").lower()

 # Vérification de la validité de l'entrée
        if len(lettre) != 1 or not lettre.isalpha():
            print("Veuillez entrer une seule lettre valide.")
            continue

 # Vérification si la lettre a déjà été proposée
        if lettre in lettres_trouvees:
            print("Vous avez déjà essayé cette lettre.")
            continue

        lettres_trouvees.add(lettre) # Ajout de la lettre aux tentatives

 # Vérification si la lettre est dans le mot
        if lettre in mot_a_trouver:
            print("Bien joué ! Cette lettre est dans le mot.")
        else:
            tentatives -= 1 # Réduction du nombre de tentatives
            print(f"Raté ! Il vous reste {tentatives} tentatives.")

 # Vérification si toutes les lettres du mot ont été trouvées
        if all(l in lettres_trouvees for l in mot_a_trouver):
            print("Félicitations ! Vous avez trouvé le mot :", mot_a_trouver)
            return

    print("Dommage, vous avez perdu ! Le mot était :", mot_a_trouver)


if __name__ == "__main__":
    jeu_devine_mot()
