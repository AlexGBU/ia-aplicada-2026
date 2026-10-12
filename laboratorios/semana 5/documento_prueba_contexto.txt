| Texto | Idioma | Caracteres | Tokens | Caracteres por token |
| :--- | :--- | :---: | :---: | :---: |
| **Frase corta** | Español | 54 | 10 | 5.40 |
| **Frase corta** | Inglés | 52 | 8 | 6.50 |
| **Párrafo de ~100 palabras** | Español | 620 | 125 | 4.96 |
| **Párrafo de ~100 palabras** | Inglés | 580 | 102 | 5.69 |

| Temp. | Ejec. | Respuesta | ¿Idéntica? |
| :---: | :---: | :--- | :---: |
| **0** | 1 | Un firewall es un sistema de seguridad que controla el tráfico de red y bloquea accesos no autorizados. | No aplica |
| **0** | 2 | Un firewall es un sistema de seguridad que controla el tráfico de red y bloquea accesos no autorizados. | Sí |
| **0** | 3 | Un firewall es un sistema de seguridad que controla el tráfico de red y bloquea accesos no autorizados. | Sí |
| **0.7** | 1 | Un firewall es un sistema de seguridad que filtra el tráfico de red para bloquear accesos no autorizados. | No aplica |
| **0.7** | 2 | Un firewall es una barrera de seguridad que supervisa el tráfico de red y bloquea conexiones no autorizadas. | No |
| **0.7** | 3 | Un firewall es un sistema de seguridad que controla el tráfico entrante y saliente de una red. | No |
| **1.5** | 1 | Es un sistema de seguridad que filtra el tráfico de red para prevenir accesos no autorizados. | No aplica |
| **1.5** | 2 | Un firewall actúa como guardián digital, revisando cada paquete de datos antes de permitirle cruzar la frontera de tu red. | No |
| **1.5** | 3 | Muralla invisible que separa tu red del caos exterior, decidiendo qué tráfico entra, qué sale y qué queda vetado. | No |

| Intento | Copias del texto | Tokens aproximados | Respuesta del modelo | ¿Fue correcta? |
| :---: | :---: | :---: | :---: | :---: |
| **1** | 1 copia | 1,150 | AZUL-7342 | Sí |
| **2** | 2 copias | 2,300 | AZUL-7342 | Sí |
| **3** | 4 copias | 4,600 | AZUL-7342 | Sí |
| **4** | 8 copias | 9,200 | AZUL-7342 | Sí |

| Posición de la aguja | Respuesta del modelo | ¿Fue correcta? |
| :--- | :---: | :---: |
| **Inicio (Párrafo 1)** | AZUL-7342 | Sí |
| **Mitad (En medio del texto)** | AZUL-7342 | Sí |
| **Final (Último párrafo)** | AZUL-7342 | Sí |
