# backup-linux

📂 Configurazione di una cartella di backup
Hai creato una cartella sicura per i backup in /opt/backup:

```bash
sudo mkdir -p /opt/backup
sudo chown root:root /opt/backup
sudo chmod 700 /opt/backup
```

## 📌 Spiegazione:


`mkdir -p`:crea la cartella, anche se i genitori non esistono.

`chown root:root`: la cartella è di proprietà di root.

`chmod 700`: solo root ha accesso completo (lettura, scrittura, esecuzione); gli altri non possono accedervi.

## ⏰ Cron: configurazione del servizio e del job
Hai attivato cron, il servizio di Linux per eseguire comandi a intervalli programmati.

✅ Verifica del servizio cron

```bash 
sudo systemctl status cron
```
Risultato:

Il servizio cron è attivo e funzionante.

È pronto per eseguire comandi automaticamente.

## ✏️ Modifica del crontab per root

```bash
sudo crontab -e
```
Hai scelto l’editor nano (opzione 1) e hai iniziato con un crontab vuoto. Qui puoi inserire comandi da eseguire a orari precisi.

💡 Esempio di riga crontab per backup giornaliero alle 2:00 AM:


```
0 2 * * * tar -czf /opt/backup/backup-$(date +\%F).tar.gz /home
```
Questa riga:

comprime /home

salva il file in /opt/backup

aggiunge la data al nome del file (backup-2025-05-19.tar.gz)

🛡️ Attenzione: assicurati che lo script non superi lo spazio disco o violi i permessi.



## ✅ Conclusioni
Hai:

Configurato correttamente una directory sicura per backup
 
Avviato e verificato cron

Impostato crontab per automatizzare i backup



screen shot dimostrativo
![image](https://github.com/user-attachments/assets/07f35c37-83e5-42b4-83f4-912c2adcd4c7)

