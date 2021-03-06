# ODataService
OData service integration with Angular(v4)

# Motivation

This small module is created to help to integrate your Angular 2 application 
with OData query creating system. The service that is shown in this module is called
to make life easier when you're acting with OData query's

# Usage example

Here is an example with config object passing 

```
import { OData } from './services/OData';
import { query } from './models/OData'

export class TestingOdata {
  
  protected query: query = {
    system : {
      skip : 5,
      top : 10,
      filter : {
        value : 'test',
        operators : [{
          type : 'compare',
          name : 'eq',
          value : '12'
          }]
      }
    }
  }

  constructor(
    private oData: OData
  ) {
    let testTransformQuery = this.OData.get(query); // this is function returns transformd query as query params
  }
}
```

But you can also use functions chain like syntax to transform your query

```
import { OData } from './services/OData'

export class TestingData {
  
  constructor(
    private OData: OData
  ) {
    let testing = this.OData.get();
    testing()
      .id(4)
      .select(['test1', 'test2'])
      .skip(34)
      .top(10)
      .then(
        (value: string) => {
          console.log(value);
        }
      )
  }
}

```
