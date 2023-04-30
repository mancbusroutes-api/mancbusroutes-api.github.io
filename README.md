# mancbusroutes-api.github.io
## Introduction
Welcome to the Manchester Bus Routes API!

Here you can track bus routes': Destinations, Operators, Is Circular?, Twitter, Bus Fares


Below is an example of how to fetch and return the data in python!
```py
import requests
class busstuffs():
    def get_info(route):
        route=str(route)
        data=requests.get('https://mancbusroutes-api.github.io/routes.json').json()
        for key, value in data.items():
            if key == 'routes':
                for i in value:
                    for key, busData in i.items():
                        if key==route:
                            return ('\n'.join([
                                '>-------------------------------<',
                                f'Route: {route}',
                                f'Route Dest: {busData["dest"]}',
                                f'Operator: {busData["operator"]}',
                                f'Fare - Child: {busData["bus_fare"]["child"]}, Adult: {busData["bus_fare"]["adult"]}',
                                f'Twitter: {busData["twitter"]}',
                                f'Is Circular?: {busData["circular"]}',
                                '>-------------------------------<'
                            ]))
        return f"No information found for route '{route}'"
    def text(route):
        return busstuffs.get_info(route)

route=str(input('Route: '))                            
data=busstuffs.text(route)
print(data)
```
