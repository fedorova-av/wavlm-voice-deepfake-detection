# wavlm-voice-deepfake-detection

Детекция голосовых дипфейков на основе предобученной WavLM Large.
Исследуется применимость WavLM как экстрактора признаков для антиспуфинга:
вклад отдельных слоёв, стратегии их агрегации и обобщение на незнакомые атаки.

## Данные
- Обучение и валидация: ASVspoof 2019 LA (train / dev)
- Финальная оценка: ASVspoof 2021 LA (eval)

## Структура
- `eda-wavlm.ipynb` - разведочный анализ данных
- `baseline-wavlm.ipynb` - baseline: последний слой WavLM + линейный классификатор
- `experiments-wavlm_part1.ipynb` - обучение на 2019 LA: weighted sum, послойный анализ, MLP, fine-tuning, RawBoost
- `experiments-wavlm_part2_final.ipynb` - оценка на 2021 LA: метрики, разбор по атакам, t-SNE

## Метод
WavLM Large (заморожена) - агрегация скрытых состояний 25 слоёв - лёгкий классификатор.
Метрики: EER (основная), min-tDCF (официальная ASVspoof).

## Основные результаты
- Weighted Sum + Linear: dev EER ≈ 0.11%
- Наиболее информативны слои T6–T12
- ASVspoof 2021 LA eval: EER ≈ 6.8%
