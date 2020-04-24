# Practica-CCNA2v7
### Escenario:
Su Jefatura le ha encargado el diseño de una propuesta de red corporativa para la nueva sucursal
de la Compañía. 
Dentro de las características solicitadas, están la alta disponibilidad de los recursos de red a través 
de redundancia, tanto de equipos como de medios de red. 
Además de la implementación de Vlans y protocolos de enrutamiento confiables.
Luego de realizar el diseño de la red en base al modelo jerárquico, solo queda la configuración de
los equipos y de los protocolos necesarios para el cumplimiento de las necesidades.

### REQUERIMIENTOS
#### Direcciones VLANS:
- **VLAN 4: 10.10.4.0/24**
- **VLAN 9: 10.10.9.0/25**
- **VLAN 13: 10.10.13.0/26**
- **VLAN 14: 10.10.14.0/28**

#### **Configuración de VLAN en SW1, SW2, SW3 y BR2.**
- Cree las VLAN 4 (Gerencia), 9 (Contabilidad), 13 (Ingenieria), y 14 (Soporte).

- Configure los puertos troncales, considerando la vlan 111 como nativa, permitiendo solo
las vlan de datos y desactivando el protocolo DTP.

- Configure los puertos de acceso de acuerdo a lo mostrado en la topología.

- Deshabilite los puertos no utilizados.

- Configure la interfaz SVI para la vlan de Soporte de acuerdo a lo mostrado en el cuadro
siguiente:
| **SW1** | **SW2** | **SW3** |
| :---: | :---: | :---: | 
|Direccion SVI | 10.10.14.3/28 | 10.10.14.4/28 | 10.10.14.5/28

- Configure como Gateway por defecto la dirección 10.10.14.14

- Verifique la configuración con el comando **show interface trunk**.

#### **Configuración de Árbol de Expansión en SW1, SW2, SW3 y BR2.**
- Configure el modo de árbol de expansión RAPID-PVST para todos los switches, incluyendo
al switch capa 3 BR2.

- Configure el switch **SW3** para que sea root primary para las VLAN 4, 9 y 13,
y root secondary para la VLAN 14.

- Configure el switch **BR2** con prioridad 24576 para la VLAN 14, y con prioridad 28672 para
las VLAN 4, 9 y 13.

- Configure los puertos que correspondan para que pasen inmediatamente al estado de
reenvío al iniciar el switch.

- Verifique la configuración mediante el comando show spanning-tree.

##### **Configuración de EtherChannels en SW1, SW2 y SW3.**
- Utilice la siguiente tabla para formar EtherChannels en los puertos de switch indicados en
la topología:
| Port-Channel | Protocolo |
| :--: | :--: |

- Revise que las interfaces port-channel estén configuradas como troncales.

- Verifique la configuración mediante el comando **show etherchannel summary**.

#### **Configuraciones de BR1, BR2 y R-CORE:**
1. Configure SSH:
   - Establezca prueba1.com como nombre de dominio.
   - Genere una clave RSA de 1024 bits.
   - Establezca la versión 2 del protocolo.
   - Configure un timeout de 50 seg.
   - Establezca un máximo de 3 reintentos de acceso.
   - Configure las líneas VTY para el acceso por SSH.
   - Use los perfiles de usuarios locales para la autenticación.
   - Cree un usuario admin1 y use la contraseña cifrada “cisco”.

2. Aplique enrutamiento de VLAN en el router BR1. Habilite y configure las subinterfaces con
     los siguientes requisitos:
   - Nombre la subinterfaz con el número de la vlan (ej. G0/0.4)
   - Configure la encapsulación dot1q apropiada.
   - Asigne la primera dirección IP del rango:
     | | VLAN 4 | VLAN 9 | VLAN 13 | VLAN 14 |
     | :--: | :--:   | :--:   | :--:    | :--:    |
     | Direccion IP | 10.10.4.1/24 | 10.10.9.1/25 | 10.10.13.1/26 | 10.10.14.1/28 |

3. Aplique enrutamiento de VLAN en el switch capa 3 BR2. Habilite y configure las SVI con
     los siguientes requisitos:
   - Nombre la SVI con el número de la vlan (ej. Interface vlan 4)
   - Asigne en BR2 la segunda dirección IP del rango:
     | | VLAN 4 | VLAN 9 | VLAN 13 | VLAN 14 |
     | :--: | :--:   | :--:   | :--:    | :--:    |
     | Direccion ip | 10.10.4.2/24 | 10.10.9.2/25 | 10.10.13.2/26 | 10.10.14.2/28 |

4. Direccione las interfaces seriales, gigaethernet y loopback de acuerdo a lo indicado en la
     siguiente tabla:
     | | R-CORE | BR1 |  BR2 |
     | :--: | :--:   | :--:   | :--:    |
     | G0/1 | 20.20.20.2/30 | 20.20.20.1/30 | -- |
     | S0/0/1 | 20.20.20.9/30 | -- | -- |
     | G0/0 | 20.20.20.5/30 | -- | -- |
     | G0/2 | -- | -- | 20.20.20.6/30 |

#### **(El router ISP y el servidor DNS/WEB ya se encuentran configurados)**
1. Configure OSPFv2 con los siguientes requisitos:
   - Utilice la ID de proceso 1 y número de área 0
   - Anuncie las redes correspondientes.
2. Verifique el enrutamiento con el comando **show ip route**.

#### **Configuración de FHRP en BR1 y BR2:**
- Configure el grupo 5 HSRP entre el BR1 y el BR2 para los equipos de las Vlan 4, 9, 13 y 14.

- Utilice la última IP de la red como Gateway Virtual.

- Asegure que el **BR1** sea el router activo para las Vlan 4 Y 9, y standby para las vlan 13 y
14.

- **BR2 debe ser activo para las Vlan 13 y 14, y standby para las vlan 4 y 9.**

- Las prioridades a utilizar son 110 y 90 según corresponda.

-  Al recuperarse de una falla, el router activo debe recuperar su rol.

- Verifique el comportamiento del grupo HSRP con el comando **show standby brief**.

#### Equipos Finales:
- Aplique configuración IP a los equipos finales asignando cualquier dirección IP disponible
dentro del rango.

- Asigne la puerta de enlace correspondiente.

- Agregue la dirección del servidor DNS.

#### Conectividad:
- Todos los computadores deben poder acceder al servidor Web y hacer ping a los otros
computadores.












