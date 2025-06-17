# Исследование методов обучения для Automatic Speech Recognition (ASR)

**Автор:** Е.В. Серова (Вологодский государственный университет)  
**Дата:** 2023  

## Описание проекта

В этом репозитории представлена работа «Исследование методов обучения для Automatic Speech Recognition (ASR)». В ней проводится обзор и сравнительный анализ шести современных подходов к обучению систем распознавания речи:

- **SpeechStew**  
- **Noisy Student Training**  
- **Conformer**  
- **ContextNet**  
- **W2V-BERT**  
- **Conv + Transformer + wav2vec2.0 + pseudo labeling**

В качестве основной тестовой площадки используется корпус **LibriSpeech** (960 часов размеченной речи + unlab-60k).

## Краткий обзор методов

| Метод                                       | Особенности                                                    |
| ------------------------------------------- | -------------------------------------------------------------- |
| **SpeechStew**                              | Объединение всех доменов + дообучение                          |
| **Noisy Student**                           | Самообучение с фильтрацией и балансировкой                     |
| **Conformer**                               | Сверточно-трансформер с относительным позиционным кодированием |
| **ContextNet**                              | RNN-Transducer с «squeeze-&-excitation»                        |
| **W2V-BERT**                                | Контрастное + маскированное предобучение                       |
| **Conv+Transformer+wav2vec2.0+pseudoLabel** | Объединение предварительного обучения и псевдо-маркировки      |

## Основные результаты

| Модель           | WER clean (no LM) | WER other (no LM) | WER clean (with LM) | WER other (with LM) |
| ---------------- | ----------------- | ----------------- | ------------------- | ------------------- |
| SpeechStew (L)   | 2.0 %             | 4.0 %             | —                   | —                   |
| SpeechStew (XXL) | 1.7 %             | 3.3 %             | —                   | —                   |
| Conformer (L)    | 2.1 %             | 4.3 %             | 1.9 %               | 3.9 %               |
| ContextNet + NST | 1.7 %             | 3.7 %             | 1.7 %               | 3.4 %               |
| Wav2Vec XXL      | 1.4 %             | 2.5 %             | 1.4 %               | 2.5 %               |

**Вывод:** наилучшие результаты достигаются у Wav2Vec XXL и Conformer + LM, но псевдомаркировка (NST) и многодоменное обучение (SpeechStew) дают конкурентоспособные показатели при ограниченных размеченных данных.

## Литература
Chan W. et al. SpeechStew: Simply Mix All Available Speech Recognition Data…

Park D.S. et al. Improved Noisy Student Training for ASR

Gulati A. et al. Conformer: Convolution-augmented Transformer…

Han W. et al. ContextNet: Improving CNNs for ASR…

Chung Y.-A. et al. W2v-BERT: Combining Contrastive Learning…

Xu Q. et al. Self-training and Pre-training are Complementary…

Panayotov V. et al. LibriSpeech: An ASR corpus based on public domain audiobooks
