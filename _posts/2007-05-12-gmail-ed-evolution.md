---
title: Gmail ed Evolution
author: ilbonzo
layout: post
permalink: /2007/05/12/gmail-ed-evolution/
dsq_thread_id:
  - 1098409974
categories:
  - linux
---
Oggi ho impostato [Evolution][1] per scaricare la posta da [Gmail][2] ed ho visto che nella pagina di aiuto del sistema di [Google][3] le istruzioni per il client di posta predefinito in [gnome][4] non ci sono.  
Ecco quindi come fare:

Attiva la funzione POP nel tuo account Gmail:

Preso direttamente dalle istruzioni gmail:  
1. Accedi al tuo account Gmail.  
2. Fai clic su Impostazioni nella parte superiore di qualunque pagina Gmail.  
3. Fai clic su Inoltro e POP nel riquadro giallo Impostazioni.

4. Seleziona Attiva POP per tutti i messaggi o Attiva la funzione POP solo per i messaggi che arrivano a partire da adesso.  
5. Scegli l&#8217;azione che desideri eseguire per i messaggi Gmail che vengono richiamati tramite POP.  
[è possibile, e molto utile mantenere una copia dei messaggi nell'account Gmail, avendo un comportamento simile ad Imap ma non altrettanto potente]  
6. Configura il client POP* e quindi fai clic su Salva modifiche. 

Aprire Evolution  
Modifica -> Preferenze -> Aggiungi  
così possiamo aggiungere un nuovo account.

Selezionare il Tab:  
• Identità:  
- mettendo i vari dati e in indirizzo mail la mail che si vuole usare.

• ricezione email:  
- Server pop.gmail.com:995  
In evolution non c&#8217;è un campo apposito dove inserire la porta  
- Usare connessione sicura: Cifratura SSL  
- tipo di autenticazione: password  
<a href='http://blog.ilbonzo.org/?attachment_id=10' rel='attachment wp-att-10' title='tab ricezione mail'><img src='http://magni.me/wp-content/uploads/2007/05/g_evolution.miniatura.png' alt='tab ricezione mail' /></a>

• Invio email  
- Server: smtp.gmail.com:587  
In evolution non c&#8217;è un campo apposito dove inserire la porta  
- Usare connessione sicura: Cifratura TLS  
- Tipo: Login  
Mettendo l&#8217;username del vostro account gmail.  
<a href='http://blog.ilbonzo.org/?attachment_id=11' rel='attachment wp-att-11' title='tab invio email'><img src='http://magni.me/wp-content/uploads/2007/05/g_evolution2.miniatura.png' alt='tab invio email' /></a>

Spero che a qualcuno possa essere utile, su gmail evolution non è considerato, però è comunque un client molto usato.

<div class='kindleWidget kindleLight' >
  
</div>



 [1]: http://www.gnome.org/projects/evolution/
 [2]: http://www.gmail.com
 [3]: http://www.google.it
 [4]: http://www.it.gnome.org/index.php/Home