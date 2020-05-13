# solyd-moddle

[![Build Status](https://travis-ci.org/thesolyd/solyd-moddle.svg?branch=master)](https://travis-ci.org/thesolyd/solyd-moddle)

Read and write BPMN 2.0 diagram with blockchain, Hooks & APIs blocks to files in NodeJS and the browser.

__solyd-moddle__ uses the [BPMN 2.0 meta-model](http://www.omg.org/spec/BPMN/2.0/) with extensions for blockchain and APIs to validate the input and produce correct BPMN 2.0 XML.


## Usage

Get the library via [npm package](https://www.npmjs.org/package/solyd-moddle). Consume it in NodeJS, via UMD or bundle it for the browser using your favorite module bundler.

![BPMN2.0 with Blockchain](https://pbs.twimg.com/media/EX72K8DWAAAfvDV?format=jpg&name=4096x4096)
```javascript - Blockchain Example
const BpmnModdle = require('solyd-moddle');

main()
async function main(){
  const moddle = new BpmnModdle();


  let xmlStr = `<?xml version="1.0" encoding="UTF-8"?>
  <bpmn:definitions xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:bpmn="http://www.omg.org/spec/BPMN/20100524/MODEL" xmlns:bpmndi="http://www.omg.org/spec/BPMN/20100524/DI" xmlns:dc="http://www.omg.org/spec/DD/20100524/DC" xmlns:di="http://www.omg.org/spec/DD/20100524/DI" xmlns:pm_1="http://thesolyd.com/BPMN/2.0/Schema.xsd" xmlns:pm="http://processmaker.com/BPMN/2.0/Schema.xsd" xmlns:tns="http://sourceforge.net/bpmn/definitions/_1530553328908" xmlns:xsd="http://www.w3.org/2001/XMLSchema" targetNamespace="http://bpmn.io/schema/bpmn" exporter="SolydModeler" exporterVersion="1.0" xsi:schemaLocation="http://www.omg.org/spec/BPMN/20100524/MODEL http://bpmn.sourceforge.net/schemas/BPMN20.xsd">
    <bpmn:process id="ProcessId" name="ProcessName" isExecutable="true">
      <bpmn:startEvent id="node_4" name="Start Event" pm_1:assignment="group" pm_1:assignedUsers="" pm_1:assignedGroups="71ea4914-0bf8-43f6-8e6b-ee3cf5abc065">
        <bpmn:outgoing>node_18</bpmn:outgoing>
      </bpmn:startEvent>
      <bpmn:startEvent id="node_5" name="Start Timer Event">
        <bpmn:outgoing>node_16</bpmn:outgoing>
        <bpmn:timerEventDefinition>
          <bpmn:timeCycle>2020-05-13T13:02:00.000Z</bpmn:timeCycle>
        </bpmn:timerEventDefinition>
      </bpmn:startEvent>
      <bpmn:startEvent id="node_6" name="Blockchain Start Event" pm_1:blockchainRef="1936c2e3-1f69-4ecb-b42e-c4f2659dbd46">
        <bpmn:outgoing>node_12</bpmn:outgoing>
        <bpmn:signalEventDefinition blockchainRef="1936c2e3-1f69-4ecb-b42e-c4f2659dbd46" />
      </bpmn:startEvent>
      <bpmn:startEvent id="node_7" name="API Start Event2">
        <bpmn:outgoing>node_11</bpmn:outgoing>
        <bpmn:messageEventDefinition messageRef="node_7_message" />
      </bpmn:startEvent>
      <bpmn:scriptTask id="node_10" name="Script Task">
        <bpmn:incoming>node_11</bpmn:incoming>
        <bpmn:incoming>node_12</bpmn:incoming>
        <bpmn:incoming>node_17</bpmn:incoming>
        <bpmn:incoming>node_18</bpmn:incoming>
        <bpmn:outgoing>node_20</bpmn:outgoing>
        <bpmn:outgoing>node_3</bpmn:outgoing>
      </bpmn:scriptTask>
      <bpmn:sequenceFlow id="node_11" name="Sequence Flow" sourceRef="node_7" targetRef="node_10" />
      <bpmn:sequenceFlow id="node_12" name="Sequence Flow" sourceRef="node_6" targetRef="node_10" />
      <bpmn:manualTask id="node_15" name="Manual Task" pm_1:assignment="user_group" pm_1:assignedUsers="e4320727-3139-4703-8235-48df5a3a9a07" pm_1:assignedGroups="group-71ea4914-0bf8-43f6-8e6b-ee3cf5abc065" pm_1:assignmentLock="true">
        <bpmn:incoming>node_16</bpmn:incoming>
        <bpmn:outgoing>node_17</bpmn:outgoing>
      </bpmn:manualTask>
      <bpmn:sequenceFlow id="node_16" name="Sequence Flow" sourceRef="node_5" targetRef="node_15" />
      <bpmn:sequenceFlow id="node_17" name="Sequence Flow" sourceRef="node_15" targetRef="node_10" />
      <bpmn:sequenceFlow id="node_18" name="Sequence Flow" sourceRef="node_4" targetRef="node_10" />
      <bpmn:endEvent id="node_19" name="End Event">
        <bpmn:incoming>node_20</bpmn:incoming>
      </bpmn:endEvent>
      <bpmn:sequenceFlow id="node_20" name="Sequence Flow" sourceRef="node_10" targetRef="node_19" />
      <bpmn:endEvent id="node_2" name="Hook End Event">
        <bpmn:incoming>node_3</bpmn:incoming>
        <bpmn:messageEventDefinition messageRef="node_2_message" />
      </bpmn:endEvent>
      <bpmn:sequenceFlow id="node_3" name="Sequence Flow" sourceRef="node_10" targetRef="node_2" />
    </bpmn:process>
    <bpmn:message id="node_7_message" name="e6b53c4b-efc0-4856-8716-68e80c658751" />
    <bpmn:message id="node_2_message" name="59ee3a7f-38f0-4c56-924f-e01ad8ad77af" />
    <bpmndi:BPMNDiagram id="BPMNDiagramId">
      <bpmndi:BPMNPlane id="BPMNPlaneId" bpmnElement="ProcessId">
        <bpmndi:BPMNShape id="node_4_di" bpmnElement="node_4">
          <dc:Bounds x="100" y="460" width="36" height="36" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNShape id="node_5_di" bpmnElement="node_5">
          <dc:Bounds x="160" y="350" width="36" height="36" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNShape id="node_6_di" bpmnElement="node_6">
          <dc:Bounds x="140" y="230" width="36" height="36" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNShape id="node_7_di" bpmnElement="node_7">
          <dc:Bounds x="130" y="110" width="36" height="36" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNShape id="node_10_di" bpmnElement="node_10">
          <dc:Bounds x="460" y="210" width="116" height="76" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNEdge id="node_11_di" bpmnElement="node_11">
          <di:waypoint x="148" y="128" />
          <di:waypoint x="518" y="248" />
        </bpmndi:BPMNEdge>
        <bpmndi:BPMNEdge id="node_12_di" bpmnElement="node_12">
          <di:waypoint x="158" y="248" />
          <di:waypoint x="518" y="248" />
        </bpmndi:BPMNEdge>
        <bpmndi:BPMNShape id="node_15_di" bpmnElement="node_15">
          <dc:Bounds x="310" y="330" width="116" height="76" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNEdge id="node_16_di" bpmnElement="node_16">
          <di:waypoint x="178" y="368" />
          <di:waypoint x="368" y="368" />
        </bpmndi:BPMNEdge>
        <bpmndi:BPMNEdge id="node_17_di" bpmnElement="node_17">
          <di:waypoint x="368" y="368" />
          <di:waypoint x="518" y="248" />
        </bpmndi:BPMNEdge>
        <bpmndi:BPMNEdge id="node_18_di" bpmnElement="node_18">
          <di:waypoint x="118" y="478" />
          <di:waypoint x="518" y="248" />
        </bpmndi:BPMNEdge>
        <bpmndi:BPMNShape id="node_19_di" bpmnElement="node_19">
          <dc:Bounds x="610" y="380" width="36" height="36" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNEdge id="node_20_di" bpmnElement="node_20">
          <di:waypoint x="518" y="248" />
          <di:waypoint x="628" y="398" />
        </bpmndi:BPMNEdge>
        <bpmndi:BPMNShape id="node_2_di" bpmnElement="node_2">
          <dc:Bounds x="520" y="60" width="36" height="36" />
        </bpmndi:BPMNShape>
        <bpmndi:BPMNEdge id="node_3_di" bpmnElement="node_3">
          <di:waypoint x="518" y="248" />
          <di:waypoint x="538" y="78" />
        </bpmndi:BPMNEdge>
      </bpmndi:BPMNPlane>
    </bpmndi:BPMNDiagram>
  </bpmn:definitions>

`;


  const {
    rootElement: definitions
  } = await moddle.fromXML(xmlStr);

  //console.log(definitions,">1>>\n", definitions.rootElements,"\n>2>>>>\n", definitions.rootElements[0].flowElements)
  definitions.rootElements.forEach((item, i) => {
    if('flowElements' in item ){
      item.flowElements.forEach((item2, i2) => {
        if('eventDefinitions' in item2 && item2['$type'] == 'bpmn:StartEvent'){
          item.flowElements.forEach((item3, i3) => {
            console.log("|__-->",i3, item3)
          })
        }else{
          //
          console.log("-->",i2, item2)
        }
      });
    }else{
      console.log(i, item)
    }
  });
}

```

``` Output
--> 0 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_4',
  name: 'Start Event',
  assignment: 'group',
  assignedUsers: '',
  assignedGroups: '71ea4914-0bf8-43f6-8e6b-ee3cf5abc065' }
|__--> 0 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_4',
  name: 'Start Event',
  assignment: 'group',
  assignedUsers: '',
  assignedGroups: '71ea4914-0bf8-43f6-8e6b-ee3cf5abc065' }
|__--> 1 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_5',
  name: 'Start Timer Event',
  eventDefinitions:
   [ Base { '$type': 'bpmn:TimerEventDefinition', timeCycle: [Base] } ] }
|__--> 2 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_6',
  name: 'Blockchain Start Event',
  blockchainRef: '1936c2e3-1f69-4ecb-b42e-c4f2659dbd46',
  eventDefinitions: [ Base { '$type': 'bpmn:SignalEventDefinition' } ] }
|__--> 3 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_7',
  name: 'API Start Event2',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
|__--> 4 Base {
  '$type': 'bpmn:ScriptTask',
  id: 'node_10',
  name: 'Script Task' }
|__--> 5 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_11',
  name: 'Sequence Flow' }
|__--> 6 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_12',
  name: 'Sequence Flow' }
|__--> 7 Base {
  '$type': 'bpmn:ManualTask',
  id: 'node_15',
  name: 'Manual Task',
  assignment: 'user_group',
  assignedUsers: 'e4320727-3139-4703-8235-48df5a3a9a07',
  assignedGroups: 'group-71ea4914-0bf8-43f6-8e6b-ee3cf5abc065',
  assignmentLock: true }
|__--> 8 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_16',
  name: 'Sequence Flow' }
|__--> 9 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_17',
  name: 'Sequence Flow' }
|__--> 10 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_18',
  name: 'Sequence Flow' }
|__--> 11 Base { '$type': 'bpmn:EndEvent', id: 'node_19', name: 'End Event' }
|__--> 12 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_20',
  name: 'Sequence Flow' }
|__--> 13 Base {
  '$type': 'bpmn:EndEvent',
  id: 'node_2',
  name: 'Hook End Event',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
|__--> 14 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_3',
  name: 'Sequence Flow' }
|__--> 0 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_4',
  name: 'Start Event',
  assignment: 'group',
  assignedUsers: '',
  assignedGroups: '71ea4914-0bf8-43f6-8e6b-ee3cf5abc065' }
|__--> 1 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_5',
  name: 'Start Timer Event',
  eventDefinitions:
   [ Base { '$type': 'bpmn:TimerEventDefinition', timeCycle: [Base] } ] }
|__--> 2 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_6',
  name: 'Blockchain Start Event',
  blockchainRef: '1936c2e3-1f69-4ecb-b42e-c4f2659dbd46',
  eventDefinitions: [ Base { '$type': 'bpmn:SignalEventDefinition' } ] }
|__--> 3 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_7',
  name: 'API Start Event2',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
|__--> 4 Base {
  '$type': 'bpmn:ScriptTask',
  id: 'node_10',
  name: 'Script Task' }
|__--> 5 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_11',
  name: 'Sequence Flow' }
|__--> 6 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_12',
  name: 'Sequence Flow' }
|__--> 7 Base {
  '$type': 'bpmn:ManualTask',
  id: 'node_15',
  name: 'Manual Task',
  assignment: 'user_group',
  assignedUsers: 'e4320727-3139-4703-8235-48df5a3a9a07',
  assignedGroups: 'group-71ea4914-0bf8-43f6-8e6b-ee3cf5abc065',
  assignmentLock: true }
|__--> 8 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_16',
  name: 'Sequence Flow' }
|__--> 9 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_17',
  name: 'Sequence Flow' }
|__--> 10 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_18',
  name: 'Sequence Flow' }
|__--> 11 Base { '$type': 'bpmn:EndEvent', id: 'node_19', name: 'End Event' }
|__--> 12 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_20',
  name: 'Sequence Flow' }
|__--> 13 Base {
  '$type': 'bpmn:EndEvent',
  id: 'node_2',
  name: 'Hook End Event',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
|__--> 14 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_3',
  name: 'Sequence Flow' }
|__--> 0 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_4',
  name: 'Start Event',
  assignment: 'group',
  assignedUsers: '',
  assignedGroups: '71ea4914-0bf8-43f6-8e6b-ee3cf5abc065' }
|__--> 1 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_5',
  name: 'Start Timer Event',
  eventDefinitions:
   [ Base { '$type': 'bpmn:TimerEventDefinition', timeCycle: [Base] } ] }
|__--> 2 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_6',
  name: 'Blockchain Start Event',
  blockchainRef: '1936c2e3-1f69-4ecb-b42e-c4f2659dbd46',
  eventDefinitions: [ Base { '$type': 'bpmn:SignalEventDefinition' } ] }
|__--> 3 Base {
  '$type': 'bpmn:StartEvent',
  id: 'node_7',
  name: 'API Start Event2',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
|__--> 4 Base {
  '$type': 'bpmn:ScriptTask',
  id: 'node_10',
  name: 'Script Task' }
|__--> 5 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_11',
  name: 'Sequence Flow' }
|__--> 6 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_12',
  name: 'Sequence Flow' }
|__--> 7 Base {
  '$type': 'bpmn:ManualTask',
  id: 'node_15',
  name: 'Manual Task',
  assignment: 'user_group',
  assignedUsers: 'e4320727-3139-4703-8235-48df5a3a9a07',
  assignedGroups: 'group-71ea4914-0bf8-43f6-8e6b-ee3cf5abc065',
  assignmentLock: true }
|__--> 8 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_16',
  name: 'Sequence Flow' }
|__--> 9 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_17',
  name: 'Sequence Flow' }
|__--> 10 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_18',
  name: 'Sequence Flow' }
|__--> 11 Base { '$type': 'bpmn:EndEvent', id: 'node_19', name: 'End Event' }
|__--> 12 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_20',
  name: 'Sequence Flow' }
|__--> 13 Base {
  '$type': 'bpmn:EndEvent',
  id: 'node_2',
  name: 'Hook End Event',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
|__--> 14 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_3',
  name: 'Sequence Flow' }
--> 4 Base {
  '$type': 'bpmn:ScriptTask',
  id: 'node_10',
  name: 'Script Task' }
--> 5 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_11',
  name: 'Sequence Flow' }
--> 6 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_12',
  name: 'Sequence Flow' }
--> 7 Base {
  '$type': 'bpmn:ManualTask',
  id: 'node_15',
  name: 'Manual Task',
  assignment: 'user_group',
  assignedUsers: 'e4320727-3139-4703-8235-48df5a3a9a07',
  assignedGroups: 'group-71ea4914-0bf8-43f6-8e6b-ee3cf5abc065',
  assignmentLock: true }
--> 8 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_16',
  name: 'Sequence Flow' }
--> 9 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_17',
  name: 'Sequence Flow' }
--> 10 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_18',
  name: 'Sequence Flow' }
--> 11 Base { '$type': 'bpmn:EndEvent', id: 'node_19', name: 'End Event' }
--> 12 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_20',
  name: 'Sequence Flow' }
--> 13 Base {
  '$type': 'bpmn:EndEvent',
  id: 'node_2',
  name: 'Hook End Event',
  eventDefinitions: [ Base { '$type': 'bpmn:MessageEventDefinition' } ] }
--> 14 Base {
  '$type': 'bpmn:SequenceFlow',
  id: 'node_3',
  name: 'Sequence Flow' }
1 Base {
  '$type': 'bpmn:Message',
  id: 'node_7_message',
  name: 'e6b53c4b-efc0-4856-8716-68e80c658751' }
2 Base {
  '$type': 'bpmn:Message',
  id: 'node_2_message',
  name: '59ee3a7f-38f0-4c56-924f-e01ad8ad77af' }


```

```javascript - Standard
import BpmnModdle from 'solyd-moddle';

const moddle = new BpmnModdle();

const xmlStr =
  '<?xml version="1.0" encoding="UTF-8"?>' +
  '<bpmn2:definitions xmlns:bpmn2="http://www.omg.org/spec/BPMN/20100524/MODEL" ' +
                     'id="empty-definitions" ' +
                     'targetNamespace="http://bpmn.io/schema/bpmn">' +
  '</bpmn2:definitions>';


const {
  rootElement: definitions
} = await moddle.fromXML(xmlStr);

// update id attribute
definitions.set('id', 'NEW ID');

// add a root element
const bpmnProcess = moddle.create('bpmn:Process', { id: 'MyProcess_1' });
definitions.get('rootElements').push(bpmnProcess);

// xmlStrUpdated contains new id and the added process
const {
  xml: xmlStrUpdated
} = await moddle.toXML(definitions);
```


## Resources

* [Issues](https://github.com/thesolyd/solyd-moddle/issues)
* [Examples](https://github.com/thesolyd/solyd-moddle/tree/master/test/spec/xml)
* [Changelog](./CHANGELOG.md)


## Building the Project

To run the test suite that includes XSD schema validation you must have a Java JDK installed and properly exposed through the `JAVA_HOME` variable.

Execute the test via

```
npm test
```

Perform a complete build of the application via

```
npm run all
```


## Related

The library is built on top of [moddle](https://github.com/bpmn-io/moddle) and [moddle-xml](https://github.com/bpmn-io/moddle-xml).


## License

Use under the terms of the [MIT license](http://opensource.org/licenses/MIT).
