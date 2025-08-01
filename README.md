# 🔐 Cryptage César en Python

## 📜 C'est quoi ?
Le cryptage César est une vieille méthode pour cacher un message.  
On remplace chaque lettre par une autre, en avançant dans l’alphabet.  
Le nombre de lettres à avancer s’appelle **la clé**.

Exemple avec une clé de 3 :
- `A` → `D`
- `B` → `E`
- `C` → `F`
- `D` → `G`

Donc **CHAT** devient **FKDW**.

---

## ⚙ Comment ça marche ?
1. Choisir un nombre (la clé).  
2. Chaque lettre du message avance de ce nombre dans l’alphabet.  
3. Si on dépasse `Z`, on revient au début (`A`).  
4. Pour lire le message, on fait la même chose mais en reculant.

---

## 💻 Ce que fait le programme
- Demande un texte à crypter ou à décrypter.
- Demande la clé (le nombre de décalage).
- Donne le texte crypté ou décrypté.
- Garde les caractères spéciaux (espaces, ponctuation…).

---

## 📂 Exemple de code
```python
def cesar(message, decalage):
    resultat = ""
    for char in message:
        if char.isalpha():
            base = ord('A') if char.isupper() else ord('a')
            resultat += chr((ord(char) - base + decalage) % 26 + base)
        else:
            resultat += char
    return resultat

texte = input("Message : ")
cle = int(input("Décalage : "))

chiffre = cesar(texte, cle)
print("Crypté :", chiffre)
print("Décrypté :", cesar(chiffre, -cle))
