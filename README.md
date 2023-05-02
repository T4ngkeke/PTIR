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
pseudocode:

on Init
  public chain ← publicly known blocks
  private chain ← publicly known blocks
  privateBranchLen ← 0
  Mine at the head of the private chain.
  
on My pool found a block
  ∆prev ← length(private chain) − length(public chain)
  append new block to private chain
  privateBranchLen ← privateBranchLen + 1
  if ∆prev = 0 and privateBranchLen = 2 then            (Was tie with branch of 1)
    publish all of the private chain                    (Pool wins due to the lead of 1)
    privateBranchLen ← 0
    Mine at the new head of the private chain.
    
on Others found a block
  ∆prev ← length(private chain) − length(public chain)
  append new block to public chain
  if ∆prev = 0 then                             (they win)
    private chain ← public chain
    privateBranchLen ← 0
  else if ∆prev = 1 then
    publish last block of the private chain         (Now same length. Try our luck)
  else if ∆prev = 2 then
    publish all of the private chain                  (Pool wins due to the lead of 1)
    privateBranchLen ← 0 
  else
    publish first unpublished block in private block.       (∆prev > 2)
Mine at the head of the private chain.
