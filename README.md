# Una ligera introducción a Arbitrum

#### P: ¡Hola! ¿Qué es Arbitrum?

¡Hola! Arbitrum es una suite de tecnología diseñada para escalar Ethereum. Puedes usar las cadenas de Arbitrum para hacer todo lo que haces en Ethereum — usar aplicaciones Web3, desplegar contratos inteligentes, etc., pero tus transacciones serán más baratas y rápidas. Nuestro producto estrella — Arbitrum Rollup, es un rollup optimista que hereda la seguridad a nivel de Ethereum.

#### P: ¿Qué, qué es “Ethereum”? ¿Qué es un “contrato inteligente”? ¿Dónde estoy?

Si aún no estás familiarizado con el ecosistema de Ethereum, puedes visitar [ethereum.org](https://ethereum.org/es/learn/) para obtener una introducción. Vuelve cuando estés listo, sin apuros.

#### P: **Dijiste que Arbitrum existe para “escalar” Ethereum; ¿por qué Ethereum necesita esta ayuda? ¿Hay algo mal con Ethereum?**

Ethereum es increíble; sin embargo, por sí solo, también tiene limitaciones. La cadena de bloques de Ethereum solo permite aproximadamente **20-40 transacciones por segundo (TPS)** en total para todos los usuarios de Ethereum. Cuando se alcanza este límite, los usuarios compiten entre sí para que sus transacciones se incluyan, lo que aumenta las tarifas.

#### P: **¿Por qué Ethereum tiene un TPS tan bajo?**

Esta fue una decisión deliberada en el diseño de Ethereum. Ethereum requiere que sus nodos (computadoras que ejecutan el software de Ethereum) lleguen a un consenso sobre el estado actual de las cosas. La forma en que lo hacen es procesando cada transacción en la historia de Ethereum. En otras palabras, si alguna vez has utilizado Ethereum, cada nodo completo de Ethereum tiene una copia de tus transacciones en su historial de registros de blockchain.\
Uno de los principios de la comunidad de Ethereum, como sistema abierto, descentralizado y peer-to-peer (par a par), es que debería ser razonablemente accesible para que cualquiera ejecute un nodo de Ethereum y valide la cadena por sí mismo. Si se vuelve demasiado costoso (en términos de requisitos de hardware/recursos computacionales), esto socava el objetivo fundamental de la descentralización. La combinación de estos dos factores (cada nodo debe procesar cada transacción y queremos que sea relativamente factible ejecutar un nodo) significa que las transacciones en Ethereum deben tener un límite de rendimiento bastante bajo.

#### P: ¿Y Arbitrum Rollup soluciona esto?

¡Claro que sí! La idea básica es esta: una cadena Arbitrum Rollup se ejecuta como una especie de submódulo dentro de Ethereum. A diferencia de las transacciones regulares de Ethereum de capa 1 (L1), no requerimos que los nodos de Ethereum procesen cada transacción de Arbitrum; más bien, Ethereum adopta una actitud de "inocente hasta que se demuestre lo contrario" hacia Arbitrum. En un principio, la Capa 1 "asume de manera optimista" que la actividad en Arbitrum sigue las reglas adecuadas. Si se produce una violación (es decir, alguien reclama "ahora tengo todo tu dinero"), esta reclamación puede ser impugnada en L1; se demostrará el fraude, se desestimará la reclamación inválida y la parte maliciosa será penalizada financieramente.

Esta capacidad para adjudicar y demostrar fraude en L1 es la característica fundamental clave de Arbitrum, y es cómo y por qué el sistema hereda la seguridad de Ethereum.

#### P: Entonces, ¿podemos usar Ethereum para demostrar fraude en Arbitrum? ¡Genial! Pero, si se comete fraude, ¿podemos estar absolutamente seguros de que podremos probarlo? Sí, de hecho, podemos estarlo. Aquí es donde entra la parte de "rollup". Los datos que se alimentan en una cadena Arbitrum Rollup (es decir, los datos de transacción del usuario) se publican directamente en Ethereum. Por lo tanto, siempre que Ethereum mismo esté funcionando de manera segura, cualquier persona interesada tiene visibilidad de lo que está sucediendo en Arbitrum y tiene la capacidad de detectar y probar fraude.

#### P: ¿Quién realiza realmente este trabajo (de verificar el fraude, demostrarlo, etc.)? Las partes que hacen avanzar el estado de la cadena Arbitrum en L1, es decir, hacer reclamaciones sobre el estado de la cadena, impugnar las reclamaciones de otros, etc., se llaman validadores. En la práctica, no esperamos que el usuario promedio de Arbitrum esté interesado en ejecutar un validador, al igual que el usuario promedio de Ethereum típicamente no ejecuta su propio nodo de validación de capa 1. Sin embargo, la propiedad crucial es que cualquiera puede hacerlo; convertirse en un validador de Arbitrum no requiere ningún permiso especial (una vez que se levanta la lista de permisos), solo que un usuario ejecute el software de validación de código abierto (y apueste Ether cuando/necesite tomar acción).

Además, siempre que haya al menos un validador honesto, la cadena permanecerá segura; es decir, solo se necesita un denunciante no malicioso para atrapar a cualquier número de alborotadores maliciosos. Estas propiedades juntas hacen que el sistema sea "sin confianza"; los usuarios no dependen de ninguna parte designada especial para que sus fondos estén seguros.

#### P: Y exactamente, ¿cómo se "demuestra" el "fraude"? Suena complicado. Oh, no es tan malo. En esencia: si dos validadores no están de acuerdo, solo uno de ellos (como máximo) puede estar diciendo la verdad. En una disputa, los dos validadores juegan un juego interactivo de llamadas y respuestas, en el que reducen su disputa a un solo paso computacional (piense en algo pequeño y simple, como multiplicar dos números). Este paso se ejecuta en L1 y, por necesidad, demostrará que la parte honesta estaba diciendo la verdad. Para obtener un análisis más detallado, consulte aquí.

#### P: Este juego de disputa obviamente lleva un tiempo; ¿esto impone algún tipo de retraso en las transacciones de los usuarios de Arbitrum? El único retraso que siente un usuario es al "retirar" —mover sus fondos de Arbitrum de regreso a Ethereum—; si los usuarios están retirando directamente de Arbitrum a Ethereum, generalmente deben esperar 1 semana antes de recibir sus fondos en L1. Sin embargo, si los usuarios utilizan una aplicación de puente rápido, pueden evitar por completo este período de espera (probablemente por una pequeña tarifa). Cualquier otra acción que realice un usuario, es decir, depositar fondos desde Ethereum a Arbitrum o usar una aplicación descentralizada (dapp) implementada en una cadena Arbitrum, no incurre en este período de espera.

#### P: Bien, volviendo atrás: la parte de "ejecución optimista" es cómo y por qué Arbitrum puede ofrecer tarifas bajas, ¿verdad? Principalmente, sí, este es el corazón de donde provienen los ahorros. Sin embargo, hay varios otros medios por los cuales Arbitrum alivia la carga en L1, todos los cuales se traducen en costos de transacción más bajos para los usuarios finales. Por un lado, las transacciones de Arbitrum se envían en lotes en L1; típicamente, un solo lote (enviado en una sola transacción L1) contendrá varias transacciones L2. La agrupación amortiza el costo general de interactuar con L1, y por lo tanto, ofrece ahorros significativos sobre la publicación de transacciones individuales a la vez. Además, los datos de transacción se publican en L1 en forma comprimida (y solo se descomprimen dentro del entorno L2), minimizando aún más la huella de la transacción en L1.

#### P: En cuanto a la experiencia de usar Arbitrum: cuando dijiste que es muy similar a usar Ethereum... Realmente lo quisimos decir, sí. Los diferentes protocolos de capa 2 enfatizan y optimizan diferentes aspectos; Arbitrum se creó con la compatibilidad de Ethereum como una prioridad principal. Esto significa que los usuarios pueden usar Arbitrum con todas sus billeteras Ethereum favoritas; los desarrolladores pueden construir y desplegar contratos con todas sus bibliotecas y herramientas de Ethereum favoritas; de hecho, la mayor parte del tiempo, la experiencia de usar Arbitrum se sentirá idéntica a la de usar Ethereum (con la excepción importante de que es mucho más barata y rápida).

Se realizó mucho desarrollo para lograr este nivel de compatibilidad con Ethereum. Pero en su núcleo: Arbitrum mismo utiliza un fork de Geth —la implementación de Ethereum más utilizada— con modificaciones para transformarlo en una capa 2 sin confianza. Esto significa que la mayor parte del código que se ejecuta en Arbitrum es idéntico al código que se ejecuta en Ethereum. Llamamos a este enfoque de vanguardia Nitro (los desarrolladores pueden ver el código aquí).
