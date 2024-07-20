# Sublist3r2

## 01 - Setup

```
$ git clone https://github.com/RoninNakomoto/Sublist3r2.git && \
python3 -m venv ~/environments/sublist3r2 && \
source ~/environments/sublist3r2/bin/activate && \
python -m pip install --upgrade pip && \
cd ~/sublist3r2/ && pip install -r requirements.txt && \
deactivate
```

## 02 - Usage

```
$ source ~/environments/sublist3r2/bin/activate

$ sublist3r2 -d website.com -b -t 64 -o subdomains.txt
```