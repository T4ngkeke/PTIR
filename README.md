# PTIR
Ce projet étudie la probabilité de réussite des attaques existantes(surtout «double spending» et/ou «selfish mining») dans des conditions différentes. 
Pour atteindre ce résultat, je veux réaliser un programme qui fait un grand nombre de simulations pour estimer la probabilité de réussite. (attack simulator)

# 1ère étape: proof-of-work
Pour Bitcoin, les mineurs trouvent le «nonce» d'une fonction de hachage qui correspond à une valeur donnée. Dans mon «simulateur», je conçois une fonction de hachage simple(ou utilise des fonctions existantes,sha256), et tous les sous-processus différents (qui sont considérées commme des mineurs) trouvent concurremment le «nonce». 

# double spending

+des différentes valeurs de bloc d'attente. Pour Bitcoin, si le récepteur attend 7 blocs puis confirme la transaction, est-ce plus sûr que d'attendre un seul? 
on va comparer leur probabilité. 
# selfish mining
+des différentes valeurs de puissance de calcul de chaîne publique et la chaîne privée. À quel seuil, «selfish mining» est la méthode la plus rentable? 

