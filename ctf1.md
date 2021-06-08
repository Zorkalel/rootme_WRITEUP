# my write ups

ctf01.root-me.org

```
[DIR]	AjaXplorer-2.5.5/	28-Jan-2010 10:51 	- 	 
[DIR]	basilic-1.5.14/	02-May-2007 13:49 	- 	 
[ ]	install.sql	17-Dec-2011 01:32 	411 	 
[DIR]	lcms/	15-Jun-2010 01:55 	- 	 
[DIR]	log1cms2.0/	09-May-2010 17:26 	- 	 
[ ]	manifest.xml	17-Dec-2011 01:32 	1.4K	 
[ ]	parameters.xml	17-Dec-2011 01:32 	8.5K	 
[DIR]	php-charts_v1.0/	15-Mar-2011 14:13 	- 	 
[DIR]	phptax/	26-Jun-2003 21:28 	- 	 
[ ]	sample.config_si.php	17-Dec-2011 01:32 	1.7K	 
[DIR]	sugarcrm/	17-Dec-2011 00:42 	- 	 
[ ]	web.config	17-Dec-2011 01:32 	3.8K	 
```
1. Evaluation

AjaXplorer2.5.5
quand je sui arrived dessus je suis falled sur une login/server dont j'inore les logins
alors continuons notrre recherche, et par hasard le couple admin/admin marche alors continuons 
sur le server pour voir ce qui se passe, et j'ai found des DIR !important


"conf/conf.php"
"server/conf" 
"server/logs" 
"server/users"

I founded des fichiers importants et sensibles dans les logs
http://ctf01.root-me.org/AjaXplorer-2.5.5/server/logs/log_01-16-14.txt
```
01-16-14 11:54:02	192.168.0.50	INFO	shared	Create User	user_id=admin
```
mais c'etat les logs et yavait rien de serieux ainsi je tombe sur le DIR
/server/user qui selon le fichier user.ser qui est format texte a ces infos
```a:1:{s:5:"admin";s:32:"21232f297a57a5a743894a0e4a801fc3";}``` admin:admin

rights.ser
```a:3:{s:10:"ajxp.admin";b:1;i:0;s:2:"rw";i:1;s:2:"rw";}```

#ATTENDEZ UNE NOTE
```
Command Injection OSNous avons regroupé 10 applications du monde réel dans une image ISO
 basée sur Ubuntu Desktop. Ces applications sont vulnérables aux attaques par injection
 de commandes que vous devrez rechercher et exploiter. Veuillez noter que toutes les applications
 ne sont pas sur le port 80 :) Bonne chance!
 -* Nom d'utilisateur: securitytube -* Mot de passe: 123321 Durée de la partie
```

une NMAP 
Nmap scan report for ctf01.root-me.org (212.129.28.18)
Host is up (0.13s latency).
Not shown: 993 closed ports
PORT      STATE SERVICE
22/tcp    open  ssh
80/tcp    open  http
8000/tcp  open  http-alt
8080/tcp  open  http-proxy
8081/tcp  open  blackice-icecap
8089/tcp  open  unknown
10000/tcp open  snet-sensor-mgmt


