# Vigia Eletrônico para VSNT

## Descrição

Este repositório reúne os procedimentos e os resultados da comparação de detectores de objetos para um Vigia Eletrônico destinado a Veículos de Superfície Não Tripulados (VSNT). Foram avaliados os modelos YOLOv8n, YOLO11n, YOLO26n e SSD300 na identificação de embarcações e pessoas em imagens marítimas.

A avaliação faz parte do Trabalho de Conclusão de Curso do Primeiro-Tenente Arthur Soares de Paula Junior no Curso de Aperfeiçoamento Avançado para Oficiais da Armada.

## Objetivo

Avaliar o desempenho de modelos de detecção de objetos na identificação de embarcações e pessoas em imagens marítimas, considerando a capacidade de detecção, os falsos positivos, os objetos não detectados, o nível de confiança e o tempo de processamento.

## Conjunto de imagens

Foram utilizadas 50 imagens selecionadas do conjunto MaSTr1325. A amostra contém 65 embarcações e 16 pessoas, totalizando 81 objetos anotados manualmente com caixas delimitadoras no CVAT.

O conjunto MaSTr1325 não é redistribuído neste repositório. As imagens podem ser obtidas na [página oficial do conjunto MaSTr1325](https://vicos.si/resources/mastr1325/).

## Modelos avaliados

- YOLOv8n;
- YOLO11n;
- YOLO26n; e
- SSD300 com rede VGG16.

Os modelos foram utilizados com pesos previamente treinados, sem treinamento adicional com as imagens marítimas avaliadas. As versões YOLO foram executadas com o pacote Ultralytics 8.4.117. O SSD300 foi executado por meio do Torchvision com pesos COCO V1.

## Configuração da avaliação

- Limite mínimo de confiança comum: 0,25;
- IoU mínima para correspondência com a anotação: 0,50;
- Ambiente de execução: Google Colab;
- Processamento: GPU NVIDIA Tesla T4;
- Classes avaliadas: embarcação e pessoa.

## Principais resultados

| Modelo | Precisão (%) | Recall (%) | F1 (%) | FPS aproximado |
|---|---:|---:|---:|---:|
| YOLOv8 | 97,4 | 93,8 | 95,6 | 43,56 |
| YOLO11 | 95,0 | 93,8 | 94,4 | 52,70 |
| YOLO26 | 87,7 | 87,7 | 87,7 | 50,59 |
| SSD300 | 93,7 | 72,8 | 81,9 | 20,29 |

Com o limite comum de confiança de 0,25, o YOLOv8 apresentou o melhor equilíbrio entre precisão e recall. O YOLO11 alcançou o menor tempo médio de processamento. O SSD300 apresentou a maior quantidade de objetos não detectados.

## Conteúdo do repositório

- `notebooks/`: código utilizado na preparação das imagens, execução das inferências e cálculo das métricas;
- `resultados/`: tabelas com os resultados quantitativos;
- `figuras/`: gráficos produzidos durante a avaliação; e
- `requirements.txt`: dependências utilizadas na execução.

## Observação

Os resultados estão limitados às 50 imagens avaliadas e não representam todas as condições encontradas no ambiente marítimo. A avaliação não contempla, por exemplo, todas as situações de navegação noturna, chuva, neblina ou estado do mar.

## Licença

Os códigos desenvolvidos para a avaliação são disponibilizados sob a licença MIT. As imagens do conjunto MaSTr1325 permanecem sujeitas às condições definidas pelos seus autores.
