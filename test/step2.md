## devonfw setup

Create the directory where the devonfw ide will be installed.

`mkdir devonfw`{{execute}}

`cd devonfw`{{execute}}


To install devonfw execute the following commands. More information about setting up your ide on https://devonfw.com/website/pages/docs/devonfw-ide-introduction.asciidoc.html#setup.asciidoc
`wget -c https://bit.ly/2BCkFa9 -O - | tar -xz`{{execute}}

`bash setup`{{execute}}


The installtion process may take a while.

The installation routine will ask you for a settings url. You can continue with the default settings by pressing return.

Accept the licence agreements.
`yes`{{execute}}

You can decline when asked wether you want to share data with Angular Team `N`{{execute}}

You will need to refresh your terminal in order to be able to use devon. Run `. ~/.bashrc`{{execute}}

## Install cobigen

`devon cobigen`{{execute}}

Cobigen Cli will be installed inside the software directory of your devonfw ide.

## Setting up your java project

Navigate to the 'workspaces/main/' folder in your devonfw installation directory.
`cd workspaces/main/`{{execute}}

Now you can use devon to setup a java project for you.
`devon java create com.example.application.cobigenexample`{{execute}}

Switch into the newly create project directory.
`cd cobigenexample/`{{execute}}

Goto the core of the project: 
`cd core`{{execute}}

<pre class="file" data-filename="devonfw/workspaces/main/cobigenexample/core/devonfw.yml">
openapi: 3.0.0
servers:
  - url: 'https://localhost:8081/server/services/rest'
    description: Just some data
info:
  title: Devon Example
  description: Example of a API definition
  version: 1.0.0
  x-rootpackage: com.devonfw.angular.test
paths:
  /keyvaluemanagement/v1/keyvalue/{KeyValueId}:
    x-component: keymanagement
    get:
      operationId: findKeyValue
      parameters:
        - name: KeyValueId
          in: path
          required: true
          schema:
            type: integer
            format: int64
            minimum: 0
            maximum: 50
      responses:
        '200':
          description: Any
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/KeyValue'
            text/plain:
              schema:
                type: string
        '404':
          description: Not found
  /keyvaluemanagement/v1/keyvalue/:
    x-component: keyvaluemanagement
    post:
      responses:
        '200':
          description: Any
      requestBody:
        $ref: '#/components/requestBodies/KeyValue'
      tags:
       - searchCriteria
  /shopmanagement/v1/shop/new:
    x-component: shopmanagement
    post:
      responses:
       '200':
          description: Any
      requestBody:
        $ref: '#/components/requestBodies/KeyValue'
components:
    schemas:
        KeyValue:
          x-component: keyvaluemanagement
          description: Entity definition of Key
          type: object
          properties:
            KeyValueExample:
              type: string
              maxLength: 100
              minLength: 5
    requestBodies:
        KeyValue:
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/KeyValue'
          required: true
</pre>

run:
 `devon mvn package -Dmaven.test.skip=true`{{execute}}
and
 `devon mvn clean install -Dmaven.test.skip=true`{{execute}}


Then we are going to generate the desired files with the yml:
`devon cobigen generate core/devonfw.yml`{{execute}}










