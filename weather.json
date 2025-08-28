{
  "name": "My workflow 2",
  "nodes": [
    {
      "parameters": {
        "rule": {
          "interval": [
            {
              "triggerAtHour": 6
            }
          ]
        }
      },
      "type": "n8n-nodes-base.scheduleTrigger",
      "typeVersion": 1.2,
      "position": [
        0,
        0
      ],
      "id": "5e09f049-0e56-446a-91f1-4b8a2b3ecd30",
      "name": "Schedule Trigger"
    },
    {
      "parameters": {
        "url": "https://api.weatherapi.com/v1/current.json",
        "sendQuery": true,
        "queryParameters": {
          "parameters": [
            {
              "name": "key",
              "value": "7778837a44a34c60b29191642252708"
            },
            {
              "name": "q",
              "value": "Baku"
            },
            {
              "name": "lang",
              "value": "az"
            }
          ]
        },
        "options": {}
      },
      "type": "n8n-nodes-base.httpRequest",
      "typeVersion": 4.2,
      "position": [
        208,
        0
      ],
      "id": "809b84b2-8c37-4c61-a696-dc4f669cf544",
      "name": "HTTP Request"
    },
    {
      "parameters": {
        "jsCode": "const weather = $json;\n\nconst message = `🌤️ Bakıda bu günün hava durumu:\n\n🌡️ Temperatura: ${weather.current.temp_c}°C (hiss edilən: ${weather.current.feelslike_c}°C)\n☁️ Vəziyyət: ${weather.current.condition.text}\n💨 Külək sürəti: ${weather.current.wind_kph} km/s\n🧭 Külək istiqaməti: ${weather.current.wind_dir}\n💧 Rütubət: ${weather.current.humidity}%\n👁️ Görünüş: ${weather.current.vis_km} km\n\n🕐 Yenilənmə vaxtı: ${weather.current.last_updated}\n📍 Yer: ${weather.location.name}, ${weather.location.country}`;\n\nreturn { message: message };"
      },
      "type": "n8n-nodes-base.code",
      "typeVersion": 2,
      "position": [
        384,
        0
      ],
      "id": "fa49a8d3-645d-4842-b552-e3b19d328360",
      "name": "Code",
      "alwaysOutputData": false,
      "executeOnce": false,
      "retryOnFail": false
    },
    {
      "parameters": {
        "sendTo": "arzuam-af106@code.edu.az",
        "subject": "= 🌤️ Bakı Hava Durumu - {{new Date().toLocaleDateString('az-AZ')}}",
        "message": "= {{$json.message}} ",
        "options": {}
      },
      "type": "n8n-nodes-base.gmail",
      "typeVersion": 2.1,
      "position": [
        544,
        0
      ],
      "id": "b0e572c1-920c-4a21-85ec-adc47ac720b0",
      "name": "Send a message",
      "webhookId": "fa3cb2b6-13d3-4550-a438-7dc7b67c1d87",
      "credentials": {
        "gmailOAuth2": {
          "id": "oN4zWw4cAgNLi4s6",
          "name": "Gmail account"
        }
      }
    }
  ],
  "pinData": {},
  "connections": {
    "Schedule Trigger": {
      "main": [
        [
          {
            "node": "HTTP Request",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "HTTP Request": {
      "main": [
        [
          {
            "node": "Code",
            "type": "main",
            "index": 0
          }
        ]
      ]
    },
    "Code": {
      "main": [
        [
          {
            "node": "Send a message",
            "type": "main",
            "index": 0
          }
        ]
      ]
    }
  },
  "active": false,
  "settings": {
    "executionOrder": "v1"
  },
  "versionId": "44c50c1c-aca5-4037-a3ad-bb58bc6ac2be",
  "meta": {
    "templateCredsSetupCompleted": true,
    "instanceId": "976e80d648ca25b313b8e4e603aa9b4d216a1cd553af02ba272d4ef70a7e1e0a"
  },
  "id": "JKWdU73wGP6Dzpof",
  "tags": []
}
