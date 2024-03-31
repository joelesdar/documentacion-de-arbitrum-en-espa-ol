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
