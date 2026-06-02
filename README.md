# AppraiSal and PRISM Preview Data

This repository contains preview data for the publication **"Why It Hurts: Identifying the Drivers of Negative Thoughts in Emotional Support Conversations"**.

The sample is provided to illustrate the data format, annotation schema, and conversation structure used in the project. The full dataset and accompanying code will be made publicly available upon paper acceptance.

## Repository Contents

- `AppraiSal_sample_data.json`: preview sample of emotional support conversation records.
- `LICENSE`: license terms for the preview release.

## Data Overview

`AppraiSal_sample_data.json` is a JSON object keyed by record identifiers. Each value represents one emotional support conversation instance, including:

- a triggering situation,
- a negative thought associated with that situation,
- belief-desire-intention information,
- ranked cognitive appraisal dimensions,
- a persona profile,
- the dialogue history,
- optional annotation or assignment metadata,
- a high-level genre label.

The current preview file contains 10 records and is intended for inspection, reproducibility discussion, and lightweight experimentation with the released schema. It should not be treated as the complete dataset used in the paper.

## Record Schema

Each top-level record has the following fields:

| Field | Type | Description |
| --- | --- | --- |
| `situation` | string | Brief description of the emotionally salient event or context. |
| `thought` | string | Negative thought associated with the situation. |
| `bdi` | object | Belief, desire, and intention statements linked to the situation and thought. |
| `cogapp_dims` | array | Ranked cognitive appraisal dimensions associated with the negative thought. |
| `persona_profile` | object | Persona metadata used for the conversation instance. |
| `dialogue_history` | array | Ordered therapist-patient conversation turns. |
| `prolific_info` | object | Annotation or assignment metadata, when available. |
| `assigned_genre` | string | Broad scenario genre assigned to the record. |

### `bdi`

The `bdi` field contains:

| Field | Description |
| --- | --- |
| `belief.content` | The belief held by the speaker before or during the situation. |
| `desire.content` | The desired outcome or goal. |
| `intention.content` | The intended action or plan. |

### `cogapp_dims`

`cogapp_dims` is an ordered list of appraisal labels. Each item contains:

| Field | Description |
| --- | --- |
| `rank` | Rank of the appraisal dimension for the instance, where `1` is highest. |
| `appraisal_name` | Name of the cognitive appraisal dimension. |

Example appraisal names in the preview include `self_cause`, `goal_incongruence`, `suddenness`, `norm_violation`, `coping_demand`, and `self_control`.

### `persona_profile`

The `persona_profile` field contains persona attributes such as:

- `name`
- `occupation`
- `gender`
- `education`
- `traits`
- `persona_hub`

### `dialogue_history`

`dialogue_history` is an ordered list of dialogue turns. Each turn contains:

| Field | Description |
| --- | --- |
| `speaker` | Speaker role, such as `Therapist` or `Patient`. |
| `content` | Text of the utterance. |

## Loading the Data

Example Python snippet:

```python
import json

with open("AppraiSal_sample_data.json", "r", encoding="utf-8") as f:
    data = json.load(f)

for record_id, record in data.items():
    print(record_id, record["thought"])
```

## Availability

This repository is a preview release. The full data and code for **"Why It Hurts: Identifying the Drivers of Negative Thoughts in Emotional Support Conversations"** will be made available upon paper acceptance.
