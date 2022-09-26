# Elastic APM (Application Performance Monitoring)

Elastic APM is an application performance monitoring system built on the Elastic Stack

## Elastic APM Server 

cd server-apm

Run : docker-compose -f server-apm.yml up

For down run : docker-compose -f server-apm.yml down -v --remove-orphans

## Angular Client APM

Run : ng new angular-client-apm

Install the Agent

    + npm install @elastic/apm-rum --save
    
Installing Elastic APM Angular packageedit

    + npm install @elastic/apm-rum-angular --save
    
Code 
    
    import { ApmModule, ApmService } from '@elastic/apm-rum-angular'
    @NgModule({
      imports: [BrowserModule, ApmModule],
      declarations: [AppComponent, ContactListComponent, ContactDetailComponent],
      providers: [ApmService],
      bootstrap: [AppComponent]
    })
    export class AppModule {
      constructor(service: ApmService) {
        // Agent API is exposed through this apm instance
        const apm = service.init({
          serviceName: 'angular-app',
          serverUrl: 'http://localhost:8200'
        })

        apm.setUserContext({
          'username': 'foo',
          'id': 'bar'
        })
      }
    }


## React Client APM

Run : npx create-react-app my-app --template typescript

Install the Agent

    + npm install @elastic/apm-rum --save
    
Installing Elastic APM React package

    + npm install @elastic/apm-rum-react --save 
    
Code
    
    import { init as initApm } from '@elastic/apm-rum'		
    initApm({

        // Set required service name (allowed characters: a-z, A-Z, 0-9, -, _, and space)
        serviceName: 'react-app',

        // Set custom APM Server URL (default: http://localhost:8200)
        serverUrl: 'http://localhost:8200',

        // Set service version (required for sourcemap feature)
        serviceVersion: '1.0',

        logLevel: "debug"
    })
      
    function App() {}


## Demo

