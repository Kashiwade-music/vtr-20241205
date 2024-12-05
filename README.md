# my-docker-dev-container-template

## Python by uv
- Python Install
  - `uv python install 3.11`
- make Python venv
  - `uv venv --python 3.11`
- activate
  - `source .venv/bin/activate`
  - `.venv\Scripts\activate`
- package install
  - `uv pip install -r requirements.txt`
- lock env
  - `uv pip freeze | uv pip compile - -o requirements.txt`