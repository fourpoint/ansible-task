# ansible-task
## Inicializace prostředí
Testovací prostředí vyžaduje qemu, libvirt, vagrand

Spuštění testovacího prostředí:
```bash
vagrand up
```

Odstranění testovacího prostředí:
```bash
vagrand destroy
```

## Síť
Vagrand vytváří síť 192.168.5.0/24. Jednotlivé VM spolu komunikují přes wireguard rozhraní wg0 v subnetu 10.8.0.0/24

## Firewall
Všechny VM mají přístupný pouze port 22. Vyjímka je reverzní proxy www-in která má otevřené porty 80, 443