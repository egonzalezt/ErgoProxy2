# ErgoProxy

<p align="center"><a target="_blank"><img src="./icon.png" width="200"></a></p>

ErgoProxy is a project that acts as a reverse proxy between external services and the "Gov Carpeta" service, allowing other services to securely access through the proxy.


## Description

ErgoProxy is an ASP.NET Core web application that uses the YARP (Yet Another Reverse Proxy) library to route requests to endpoints of the "Gov Carpeta" service. This project takes its name and inspiration from the anime "Ergo Proxy," where proxies are intermediary entities that connect the inhabitants of Romdo City with the outside world.

## Features

Reverse Proxy: ErgoProxy acts as a reverse proxy, receiving requests from other services and securely routing them to the "Gov Carpeta" service.

Security: Security measures are implemented to ensure that only authorized requests can access the "Gov Carpeta" service through the proxy.

## Installation and Usage

1. Clone the ErgoProxy repository.
2. Configure the appsettings.json file with the address of the "Gov Carpeta" service.
3. Run the ErgoProxy application in your development environment.
4. Other services can send requests through the ErgoProxy proxy to the endpoints of the "Gov Carpeta" service.

## Configuration

The proxy and "Gov Carpeta" service endpoints configuration is located in the `appsettings.json` file. Make sure to adjust this configuration according to the specific needs of your environment.

```json
{
  "ReverseProxy": {
    "Clusters": {
      "mycluster": {
        "Destinations": {
          "govcarpeta": {
            "Address": "https://govcarpeta-21868b7e9dd3.herokuapp.com"
          }
        }
      }
    },
    "Routes": {
      "validateCitizen": {
        "ClusterId": "mycluster",
        "Match": {
          "Path": "/apis/validateCitizen/{**catch-all}"
        }
      },
      "getOperators": {
        "ClusterId": "mycluster",
        "Match": {
          "Path": "/apis/getOperators/{**catch-all}"
        }
      },
      // Add more routes here as needed
    }
  }
}
```

## License

This project is licensed under Apache 2.0. See the [LICENSE](./LICENSE) file for more details.