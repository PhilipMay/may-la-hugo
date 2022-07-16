---
title: Colab
---

# Colab
- Colab: <https://colab.research.google.com/>
- Colab on GitHub: <https://github.com/googlecolab/colabtools>

## Shortcuts
- Show shortcuts: `ctrl + m, h`
- Insert code cell above: `ctrl + m, a`
- Insert code cell below: `ctrl + m, b`
- Delete cell/selection: `ctrl + m, d`
- Convert to code cell: `ctrl + m, y`
- Convert to markdown cell:: `ctrl + m, m`

## More
- render pandas dataframes into interactive tables: `%load_ext google.colab.data_table`

## Download Files from Colab
```python
from google.colab import files
files.download('<file_to_download>')
```

## Upload Files to Colab
```python
from google.colab import files
uploaded = files.upload()
```

## Mount Google Drive
```python
from google.colab import drive
drive.mount('/gdrive')
```

```bash
ls -la /gdrive
```
