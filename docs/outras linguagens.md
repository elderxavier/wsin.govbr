# Em Python

Pode-se usar a biblioteca suds que não gera classes.

Uma forma de utilização é:

```python
from suds.client import Client
from suds.wsse import *
from suds.xsd.doctor import Import, ImportDoctor
url = 'https://homologwsincom.in.gov.br/services/servicoIN?wsdl'
security = Security()
ns = 'http://data.xfire.ws.incom'
imp = Import(ns=ns, location=url)
imp.filter.add('http://data.xfire.ws.incom')
imp.filter.add('http://xfire.ws.incom')
doctor = ImportDoctor(imp)

token = UsernameToken('USUARIO', 'SENHA')
security.tokens.append(token)

client = Client(url, doctor=doctor)
client.set_options(wsse=security)

client.service.ConsultaTodosFeriado()
```

Com o ``` print client``` você pode ver os métodos e as classes criadas.
