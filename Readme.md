# ModernBERT Named Entity Recognition (NER) Training

A complete implementation for fine-tuning ModernBERT on Named Entity Recognition tasks using the CoNLL-2003 dataset.

Get the trained weights on -> https://huggingface.co/joe-xhedi/ModernBERT-NER

## Model Configuration

- **Base Model**: `answerdotai/ModernBERT-base`
- **Trained Model**: `joe-xhedi/ModernBERT-NER`
- **Training Epochs**: 3
- **Batch Size**: 16 (train/eval)
- **Learning Rate**: 2e-5
- **Mixed Precision**: FP16 enabled

## Output Format

The inference output shows aligned tokens and their predicted NER labels:

```
Input text: John Smith works at Google in New York.
--------------------------------------------------
Token           Label
--------------------------------------------------
[CLS]           O
John            B-PER
Smith           I-PER
works           O
at              O
Google          B-ORG
...
```

## Entity Types (CoNLL-2003)

- **PER**: Person names
- **ORG**: Organizations
- **LOC**: Locations
- **MISC**: Miscellaneous entities
- **O**: Outside (no entity)

## Customization

To use your own dataset, replace the dataset loading section:

```python
# Replace this line
dataset = load_dataset("conll2003")

# With your custom dataset
dataset = load_dataset("path/to/your/dataset")
```

## Performance

The model achieves competitive performance on CoNLL-2003 NER task with proper evaluation using seqeval metrics.

```json
{
  "eval_loss": 0.04691711440682411,
  "eval_accuracy": 0.9892527549550251,
  "eval_f1": 0.9363408521303258,
  "eval_runtime": 16.8501,
  "eval_samples_per_second": 192.877,
  "eval_steps_per_second": 12.107,
  "epoch": 3.0
}
```
