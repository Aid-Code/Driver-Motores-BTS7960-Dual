# TitanCore 7960: Driver BTS7960 Dual Channel Custom
#### Buenas! Soy Aiden, y les quise escribir un pequeño texto para comentarles de este desarrollo que hice para mi robot y para la comunidad!

## Origen
La idea inicialmente empezó porque utilizaba un Monster Shield (VNH2SP30) que no suele ser tan fácil de conseguir, y quizás si se consigue es caro, por lo que necesitaba conseguir una alternativa a este driver de motores para mi robot Sumo.  
De ahí empecé a buscar como funcionaba un **Puente H**, que componentes se usaban, que transistores usar y por qué.   
Como primer acercamiento armé un Puente H con transistores mosfet en una placa experimental, usando gate drivers, que milagrosamente funcionó (después de revisar 50 veces mis dudosas soldaduras a las 5 A.M), pero cuando hice un primer diseño de la PCB, me di cuenta que no era lo suficientemente eficiente en espacio.
No importaba cuantos componentes SMD usara, era imposible reducirla.   
Más adelante, después de un tiempo de buscar (y charlar con mi LLM de confianza) encontré que existían encapsulados que integraban dos transistores "en uno". 
A todo esto, yo ya conocía el módulo comercial del BTS7960, pero me parecía una placa gigante (con un disipador gigante) para el uso que yo le quería dar. En esta parte de mi investigación descubrí que los BTS7960 eran esos peculiares encapsulados que integraban "dos transistores en uno". Por lo que dije PERFECTO, LOS COMPRO; LOS DESUELDO; ARMO MI PLACA!  
Dicho y hecho, acá estamos!

## Funcionamiento
La dinamica de este driver de motores es un poco distinta a lo habitual, comparandola con un Monster Shield o un L298n.  
Los pines son:
- GND
- VCC --> Voltaje lógico de 3.3v a 5v
- EN_1 --> Habilita el paso de corriente al Canal 1 (Opcional conectarlo a un pin, puede ir a VCC)
- EN_2 --> Habilita el paso de corriente al Canal 2 (Opcional conectarlo a un pin, puede ir a VCC)
- PWM_A --> Señal PWM del Canal 1 en una dirección
- PWM_B --> Señal PWM del Canal 1 en dirección contraria
- PWM_C --> Señal PWM del Canal 2 en una dirección
- PWM_D --> Señal PWM del Canal 2 en dirección contraria

- VS --> Voltaje de alimentación y salida a los motores de 6v a 28v (**Aprox. basado en la datasheet del BTS7960**)

## Puesto a prueba
Hasta ahora los parametros con los que puse a prueba el funcionamiento del driver son:  
- VCC: 5v
- VS: ~15v

La idea es utilizarlo a 24v con motores que podrían llegar a consumir 11,2A por canal. Cuando lo pruebe y confirme que no explota lo comento!

## Licencia y Uso Comercial
*Este proyecto está licenciado bajo* **Creative Commons Atribución-NoComercial-CompartirIgual 4.0 Internacional (CC BY-NC-SA 4.0)**. Consulta el archivo [LICENSE](LICENSE) para más detalles.
- *Puedes clonar, fabricar, estudiar y modificar este diseño libremente para proyectos personales, educativos o de competencia.*
- *Queda terminantemente prohibida la comercialización, venta directa o integración comercial de este diseño sin autorización previa.*
- Para consultas comerciales o adquisición de módulos ensamblados, contactar a: aiden.maidp@gmail.com
