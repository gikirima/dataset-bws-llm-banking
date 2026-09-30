# dataset-bws-llm-banking

A sentiment distribution dataset of 50,000 Indonesian reviews of four mobile banking apps (BRImo, myBCA, Livin' by Mandiri, and Wondr by BNI). The reviews come from Google Play Store (49,652) and X (348). Each review has a soft label over positive, neutral, and negative sentiment.

## File

`dataset-bws-llm-banking.csv` (UTF-8, 50,000 rows)

| Column | Description |
|---|---|
| `text_id` | Review identifier |
| `review_text` | Preprocessed review text |
| `app_name` | Name of the app |
| `platform` | `Play Store` or `X (Twitter)` |
| `p_positif` | Probability of positive sentiment |
| `p_netral` | Probability of neutral sentiment |
| `p_negatif` | Probability of negative sentiment |
| `hard_label` | Label with the highest probability (`positif`, `netral`, or `negatif`) |
| `pita` | Entropy band of the soft label (`tegas` = low, `menengah` = medium, `ambigu` = high) |

The three probabilities in each row sum to 1.

## Labeling

Three large language models (MiniMax M3, Qwen3.7-Plus, and DeepSeek V4 Flash) annotated each review three times with Label Best-Worst Scaling. In each judgment, the model chose the most suitable and the least suitable sentiment label. The nine judgments were merged into a weighted relation graph, and 100 random walks on the graph produced the soft label.
