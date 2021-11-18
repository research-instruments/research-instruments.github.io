FROM python:3.9

WORKDIR /app/mkdocs
EXPOSE 8000

COPY . .

RUN pip install -r docs/requirements.txt && \
    python -m pip3 install --upgrade pip && \
    pip3 install mknotebooks


CMD ["mkdocs", "serve", "--dev-addr=0.0.0.0:8000"]
