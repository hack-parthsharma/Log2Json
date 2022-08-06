# log2json

Convert your logs into serialized JSON format

## Usage

1. Clone repository
2. Install requirements
3. Run python script

```sh
git clone https://github.com/hack-parthsharma/Log2Json.git

cd log2json

pip install -r 'requirements.txt'

python log2json.py [log-file] [output-file]
```
### Known issues
Duration is calculated from the first timestamp to the next one of the same event.
## Example
### Input
```log
2021-05-01T00:00:06.420666 170AAC5EBAD122AA message-id=<ad8f365c-c6d8-434d-879c-1dc112d4ff36@IF9HFZCQRX>
2021-05-01T00:00:07.117297 09E8698600CF8B32 client=10.192.162.239
2021-05-01T00:00:07.279394 09E8698600CF8B32 message-id=<3455937c-58c9-4dae-b057-692d4dd26684@PKCKUO0ORJ>
2021-05-01T00:00:07.319452 A87246FB7082775D status=rejected
2021-05-01T00:00:12.187672 E0039D9A55225872 to=<sarah.brown@example.com>
2021-05-01T00:00:12.387427 09E8698600CF8B32 from=<charles.brown@example.com>
2021-05-01T00:00:13.309684 0E9D8BAD6F58CF42 status=sent
2021-05-01T00:00:13.963835 2A9F9D3BA61EE478 message-id=<aebad43f-81ea-4ced-9edb-d1a6ac7552d5@TWJZEN7KX3>
2021-05-01T00:00:14.178614 09E8698600CF8B32 to=<barbara.brown@example.com>
2021-05-01T00:00:14.788593 B8FA2DB700058444 status=sent
2021-05-01T00:00:24.953721 63EFB9B68FE16222 client=2001:db8::1ea9:6da0:cd41
2021-05-01T00:00:25.670689 09E8698600CF8B32 status=rejected
2021-05-01T00:00:25.852578 80AE5FEE2A046EF8 message-id=<d41fb35b-e516-4559-8cc2-583fbaa2051b@PKCKUO0ORJ>
```
 ### Shell
```
python log2json.py logs/log.txt logs/log.json

[*] Processing data...
[*] Creating event...
[*] Sorting data by start time...
[*] Writing to file...

[‡] Fixing comma...
[‡] Fixing indent...
[‡] File log.json fixed!

[+] Results: log.json
```
### Output

```json
[
  {
    "time": {
      "start": "2021-05-01T00:00:07.117297",
      "duration": "0:00:18.553392"
    },
    "sessionid": "09E8698600CF8B32",
    "client": "10.192.162.239",
    "messageid": "<3455937c-58c9-4dae-b057-692d4dd26684@PKCKUO0ORJ>",
    "address": {
      "from": "<charles.brown@example.com>",
      "to": "<barbara.brown@example.com>"
    },
    "status": "rejected"
  }
]
````
