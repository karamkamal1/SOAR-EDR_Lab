## DETECT 

events:
  - NEW_PROCESS
  - EXISTING_PROCESS
op: and
rules:
  - op: is
    value: windows
  - op: or
    rules:
      - case sensitive: false
        op: ends with
        path: event/FILE_PATH
        value: lazagne.exe
      - case sensitive: false
        op: contains
        path: event/COMMAND_LINE
        value: lazagne
      - case sensitive: false
        op: is
        path: event/HASH
        value: 467e49f1f795c1b08245ae621c59cdf06df630fc1631dc0059da9a032858a486

  


## RESPOND

- action: report
  metadata:
    author: Karam Kamal(karamkamal1-.github,io)
    description: Detects LaZagne(SOAR-EDR TOOL)
      from view
    falsepositives:
    - Unlikely
    level: medium
    tags:
    - attack.credential_access
  name: KaramKamal1-HackTool-LaZagne)(SOAR_EDR)
