# AI_USAGE.md — Lab 5: Embeddings y búsqueda semántica

## Herramienta usada
Claude (Anthropic), por chat.

## Cómo lo usé

No le pedí a la IA que resolviera los TODO directamente. La usé para entender
conceptos antes de implementarlos, y para organizar el notebook:

1. **Por qué FastText para español:** pregunté qué diferencia hay entre FastText
   y otros modelos de embeddings, y por qué el manejo de n-gramas de caracteres
   lo hace mejor para el español (morfología, palabras fuera de vocabulario).

2. **Vector de documento como promedio:** discutí por qué promediar los vectores
   de los tokens es una aproximación razonable y cuáles son sus limitaciones —
   para entender qué estamos sacrificando antes de ver Sentence-BERT en el Lab 6.

3. **Estructura general del notebook:** pedí ayuda para organizar el andamiaje
   y conectar las partes A y B con lo que ya habíamos construido en los Labs 2, 3
   y 4, sin reescribir funciones que ya tenía funcionando.

4. **Análisis de la falla agua/hídrico:** discutí cómo los resultados de coseno
   entre vectores FastText demuestran concretamente la limitación que vimos en
   los labs anteriores con TF-IDF y el clustering.

## Qué le di a la IA
- El enunciado completo del Lab 5.
- El corpus_procesado.json real del Lab 1 (14 noticias de Chiapas).
- Las funciones de TF-IDF (Lab 2), BM25 (Lab 3) y métricas (Lab 3) para que
  el notebook las reutilizara directamente sin reescribirlas.
- Los qrels del Lab 3 para mantener la misma evaluación.

## Qué cambié o decidí yo
- Las funciones tf, idf, bm25, ndcg y las demás métricas son exactamente las
  mismas de los labs anteriores, no las modifiqué.
- Las observaciones de A.2 (vecinos sorprendentes), A.4 (analogías que
  funcionan y que fallan) y B.4 (qué consultas mejoran con el semántico y por
  qué) las escribí yo después de ver mis resultados reales al ejecutar.
- El análisis de la celda B.4 sobre en qué tipo de consultas mejora el
  buscador semántico lo hice yo a partir de los números reales de NDCG que
  me salieron, no es una respuesta genérica.

## Lo que no usé
- No usé ninguna librería de búsqueda semántica lista (como sentence-transformers
  o faiss); el buscador semántico lo construí manualmente con cos_vec y los
  vectores promediados de FastText.
- La interpretación de los grupos temáticos y la decisión sobre qué consultas
  ilustran mejor la mejora semántica las tomé yo, leyendo los resultados reales.
