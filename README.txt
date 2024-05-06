# Distributed Systems 2023-24
Semester project for the course "Distributed Systems" (NTUA, 2023-24). Developed a blockchain application (BlockChat) for exchanging money and messages. 

##  Our Team   Group: 29  
| Name  | NTUA register number (Αριθμός Μητρώου) |
| ------------- | ------------- |
|  [Dimitrios-David Gerokonstantis](https://github.com/DimitrisDavidGerokonstantis)  | el19209  |   
|  [Athanasios Tsoukleidis-Karydakis](https://github.com/ThanosTsoukleidis-Karydakis) | el19009  |
|  [Ioannis Karavgoustis](https://github.com/gkara) |  el19847 |    

## Description
Στο Backend του repo υπάρχουν οι εξής φάκελοι:

-  src5Clients : ο κώδικας για το BlockChat με 5 clients. Αυτός ο κώδικας περιέχει σχόλια και διευκρινίσεις.

- src10Clients : Η μόνη διαφορά σε αυτόν τον κώδικα είναι η δημιουργία περισσότερων αρχείων clients και η προσαρμογή κάποιων παραμέτρων. 
Κατά τα άλλα η υλοποίηση είναι ακριβώς ίδια. Ωστόσο, σε αυτόν τον φάκελο, τα αρχεία δεν περιέχουν σχόλια, οπότε για λόγους κατανόησης 
της υλοποίησης προτείνουμε να ανατρέξετε στον φάκελο src5Clients.

### ΣΗΜΕΙΩΣΗ
Η χρήση της βιβλιοθήκης multiprocessing της python απαιτεί κάποιες προσαρμογές στον κώδικα προκειμένου να τρέξει σε Windows. Ο κώδικας αυτός δουλεύει πλήρως σε Linux. 
Οι αλλαγές που χρειάζονται για την εκτέλεση σε Windows αφορούν τον ορισμό μιας συνάρτησης main και αρχικοποίηση των νημάτων σε αυτήν και όχι όπως στον κώδικα των παραπάνω φακέλων. 
Επίσης κάποιες μεταβλητές ορισμένες με χρήση managers, θα πρέπει να οριστούν σαν κοινές μεταβλητές (χωρίς χρήση managers) και να προσπελαύνονται κανονικά (χωρίς .value).
Παράδειγμα ορισμού της main για τον User1.py: 

def main():
    t = threading.Thread(target=send_coins)
    t.start()
    broadcastMinedBlockThread = threading.Thread(target=broadcastMinedBlock)
    broadcastMinedBlockThread.start()
    app.run(host=myNode.ip, port=myNode.port, debug=False)
    broadcastMinedBlockThread.join()


if name == '__main__':
    main()


Εντός των src φακέλων υπάρχει ο φάκελος cli (ενδεικτικά μόνο για έναν κόμβο, τον 0 : για χρήση σε κάθε άλλο κόμβο χρειάζεται μόνο η αλλαγή των ports στα requests των αρχείων του cli). 
Για την λειτουργία του cli, πρέπει για κάθε εντολή να ακολουθηθούν οι οδηγίες που δίνονται στην αναφορά.
Επιπλέον εντός του src υπάρχουν κάποια αρχεία cli1.py, cli2.py κλπ, τα οποία διαβάζουν τα δοθέντα inputs (trans#.txt) και δημιουργούν αυτά τα transactions.
Τέλος, υπάρχει το αρχείο run.py το οποίο τρέχει αυτόματα όλους τους κόμβους και (με αφαίρεση των τελευταίων σχολίων στον κώδικα) όλα τα αρχεία cli#.py, 
οπότε με την χρήση του εκτελούνται αυτόματα τα πειράματα της εκφώνησης. 

### Report
Επιπλέον, στο repo υπάρχει ο φάκελος :
- report : Περιέχει το .pdf αρχείο με την αναφορά και τον φάκελο LatexProject με τον κώδικα .tex σε Latex και τα χρησιμοποιούμενα images.


### ΣΧΕΤΙΚΑ ΜΕ ΤΟ FRONTEND :
Ο κώδικας του frontend (χρήση React) είναι προσαρμοσμένος να επικοινωνεί με το backend του κόμβου 0 ενδεικτικά (για χρήση του σε οποιοδήποτε άλλο κόμβο, χρειάζεται μόνο η αλλαγή
του χρησιμοποιούμενου port στα axios requests). Με npm install και npm start μπορεί να τρέξει το frontend. Σημειώνουμε ότι τα endpoints που χρησιμοποιεί το frontent
έχουν προστεθεί μόνο στα αρχεία κώδικα του src5Clients, οπότε μόνο σε αυτό το test case μπορεί να ελεχθεί η λειτουργία του. Βέβαια, εύκολα κανείς αντιγράφει αυτά τα endpoints 
και στα αρχεία κώδικα του src10Clients. 



