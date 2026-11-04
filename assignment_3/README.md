# Assignment 3 setup

Use the course Python environment and open `assignment_3.ipynb` with `assignment_3` as the working directory.

The AG News data are provided in `data/news_data.npz`: 120,000 training examples and 7,600 test examples, with labels `World`, `Sports`, `Business`, and `Sci/Tec`. The file combines each article's title and description and maps the original labels 1–4 to 0–3. The source CSV files and their checksums are documented in [PyTorch's AG News loader](https://docs.pytorch.org/text/stable/_modules/torchtext/datasets/ag_news.html).

For the GloVe exercises:

1. Download `glove.6B.zip` from the [Stanford GloVe project](https://nlp.stanford.edu/projects/glove/) or its [official Hugging Face mirror](https://huggingface.co/stanfordnlp/glove/resolve/main/glove.6B.zip).
2. Extract **`glove.6B.50d.txt`** into this `assignment_3` folder, alongside the notebook.
3. Keep `important_stuff.pkl` alongside the notebook; it is used by the initial seed-generation cell.

The GloVe vectors are a separate download and are not stored in this repository. Student implementation placeholders are intentional and must be completed before their dependent cells can run.
