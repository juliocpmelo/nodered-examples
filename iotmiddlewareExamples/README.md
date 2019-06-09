
Os exemplos abaixo usam como base um banco de dados mongo db
- Deve ser cadastrada a base iotmiddleware
- Demve ser criadas, dentro da base iotmiddleware, as coleções dispositivos e dados

Os dados são organizados no banco da seguinte forma:

- Todos os dispositivos cadastrados são inseridos na coleção dispositivos. Cada entrada desta coleção tem os campos: 
  - deviceId: nome atribuido ao dispoistivo
  - deviceToken: token gerado pelo sistema e atribuido ao dispositivo
  - sensores: vetor com todos os sensores cadastrados

- Para cada dispositivo cadastrado, existe uma entrada na coleçao dados. Esta entrada tem os campos:
  - deviceToken: token relativo ao dispositivo
  - <sensor>: um campo com o nome do sensor, para cada sensor cadastrado. Esse campo contém um vetor no formato {timestamp:tempo, valor:[<vetor de valores>]}
  
Para usar os exemplos importe no node-red usando import > clipboard > new flow. Tenha certeza também que os componentes do dashboard estão organizados da seguinte maneira:
- Login screen (disabilitado por padrão)
  - Sign-in
    - Dashboard Sign-In
- Device Manager (disabilitado por padrão)
  - New Device
    - Formulario
  - Registered Devices
    - Device
    - Edit
    - View Data
  - Device Information
    - Device Info
- Device Data (disabilitado por padrão)
  - Device Sensor
    - Sensors
  - Grafico
    - chart
- Logout (disabilitado por padrão)
  - Group 1
    - spacer 1x1

Uma vez rodando no node RED o sistema pode ser testado usando o seguinte comando da curl:

```shell
curl --header "Content-Type: application/json" --request POST http://192.168.40.101:1880/postData --data '{"deviceToken":"2mpkachz64aqn9zxa5ctq","sensor":"s4","timestamp":10,"valor":[6]}'
```

Veja que esse comando usa um dispositivo cujo token é 2mpkachz64aqn9zxa5ctq, e possui o sensor s4 cadastrado.
