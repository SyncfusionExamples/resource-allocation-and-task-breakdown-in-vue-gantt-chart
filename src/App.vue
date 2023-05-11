<template>
  <ejs-gantt :dataSource="data"
             :taskFields="taskFields"
             :treeColumnIndex="1"
             :editSettings="editOptions"
             :resources="resources"
             :resourceFields="resourceFields"
             :toolbar="toolbarOptions"
             viewType="ResourceView"
             :showOverAllocation="true"
             :enableMultiTaskbar="true"
             :labelSettings="labelOptions"
             :height="450">
    <e-columns>
      <e-column field="TaskID" headerText="Task ID" width="120" textAlign="Right"></e-column>
      <e-column field="TaskName" headerText="Task Name" textAlign="Left" width="200"></e-column>
      <e-column field="resources" width="200"></e-column>
      <e-column field="StartDate" headerText="Start Date" textAlign="Right" format="dd/MM/yyyy" width="120"></e-column>
      <e-column field="Duration" headerText="Duration" textAlign="Right" width="120"></e-column>
    </e-columns>
  </ejs-gantt>
</template>

<script>
import {GanttComponent, ColumnsDirective, ColumnDirective, Edit, Toolbar} from '@syncfusion/ej2-vue-gantt'
import {resourceData, editingResources} from './data.js'
export default{
  name: 'App',
  components: {
    'ejs-gantt': GanttComponent,
    'e-columns': ColumnsDirective,
    'e-column': ColumnDirective
  },
  provide:{
    gantt: [Edit, Toolbar]
  },
  data(){
    return{
      data: resourceData,
      editOptions:{
        allowEditing: true,
        allowAdding: true,
        mode: 'Dialog'
      },
      toolbarOptions:['Add'],
      resources:editingResources,
      resourceFields:{
        id: 'resourceId',
        name: 'resourceName'
      },
      taskFields:{
        id: 'TaskID',
        name: 'TaskName',
        resourceInfo:'resources',
        startDate: 'StartDate',
        endDate: 'EndDate',
        duration: 'Duration',
        progress: 'Progress',
        dependency: 'Predecessor',
        child: 'subtasks'
      },
      labelOptions:{
        rightLabel: 'resources',
        taskLabel: 'TaskName'
      }
    }
  }
}

</script>

<style>
  @import url("https://cdn.syncfusion.com/ej2/material.css");
</style>

