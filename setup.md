# Codespaces Setup Guide (Datathon Duolingo)

## 0) Open the repo
```bash
$BROWSER https://github.com/lab-hu/datathon-duolingo
```

## 1) Create a Codespace
1. Click **Code** → **Codespaces** tab  
2. Click **Create codespace on main**  
3. Wait for the environment to build

## 2) Open the notebook
- In the Explorer, open `analysis.ipynb`
- Select a Python kernel when prompted

## 3) Install packages (Cell 1 in notebook)
Run the first cell:
```python
%pip install pyspark pandas numpy matplotlib seaborn duckdb
```

## 4) Download the dataset (Terminal)
```bash
cd /workspaces/datathon-duolingo
gdown --fuzzy "https://drive.google.com/file/d/1sEwxn6PmG-FWva6qQAdRpM-48X4hVvc_/view?usp=drive_link" -O dataset.zip
ls -lh dataset.zip
```

**Expected size:** ~9.4GB  
If it’s tiny (KB), the download failed.

### Fallback: browser download + upload
1. Open the link in your browser and download `dataset.zip`  
2. In VS Code Explorer → right‑click folder → **Upload…**  
3. Upload `dataset.zip` into `/workspaces/datathon-duolingo`

## 5) Extract train partitions one‑by‑one (Terminal)

### Part 1
```bash
cd /workspaces/datathon-duolingo
unzip -o dataset.zip train-part-1.tar.gz
tar -xzf train-part-1.tar.gz
rm train-part-1.tar.gz
find train-part-1 -name "*.parquet"
```

### Part 2
```bash
unzip -o dataset.zip train-part-2.tar.gz
tar -xzf train-part-2.tar.gz
rm train-part-2.tar.gz
find train-part-2 -name "*.parquet"
```

### Part 3
```bash
unzip -o dataset.zip train-part-3.tar.gz
tar -xzf train-part-3.tar.gz
rm train-part-3.tar.gz
find train-part-3 -name "*.parquet"
```

### Cleanup (free space)
```bash
rm dataset.zip
df -h .
```

You should now have **3 parquet files** in:
```
train-part-1/
train-part-2/
train-part-3/
```

## 6) Run the notebook
- Run cells in order.
- Cell 6 loads a **30K sample** from all 3 partitions (safe).
- Then run EDA cells (7+).

---

## Troubleshooting
- **Kernel crashes:** restart kernel, keep sample size ≤ 50K.  
- **No parquet found:** re‑run unzip/tar for that part.  
- **Permission errors in gdown:** use browser download + upload.
