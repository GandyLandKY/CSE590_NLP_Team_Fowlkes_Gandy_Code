FROM jupyter/datascience-notebook:latest

USER root

RUN apt-get update --yes && \
    apt-get install --yes --no-install-recommends && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

USER $NB_UID

RUN pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu && \
    pip3 install --user -U nltk && \
    python -m nltk.downloader popular && \
    pip3 install --user gensim && \
    pip3 install numpy torch datasets huggingface_hub transformers trl bitsandbytes sentencepiece openai tvm peft onnx && \
    conda clean --all -f -y && \
    fix-permissions "${CONDA_DIR}" && \
    fix-permissions "/home/${NB_USER}"