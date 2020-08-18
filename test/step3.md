Now we will generate all desired classes with a yml file. 

Click on the `Copy-to-Editor`-Button in order to copy the yml-file to your project.

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


Then we are going to generate the desired files with the yml:
`devon cobigen generate devonfw.yml`{{execute}}










