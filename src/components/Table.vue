<template>
<div class="table">
  <div class="projectsHeader">
    <div>
       <p  class="projectsNumber"> {{apiData.data?.length}} Projects</p>
    </div>
    <div>
    </div>
    <div>
    </div>

    </div>
 
 <div class="tableSection">
  <table>
    <tbody>
      <tr>
        <th> Project Name</th>
        <th> Developer</th>
        <th> Area</th>
        <th> State</th>
        <th> Status</th>
        <th> Sector</th>
      </tr>
      <tr v-for="info in apiData.data" :key="info.id">
        
        <td class="firstTD">{{info?.project_name}}</td> 
        <td>{{info?.developer}}</td> 
        <td>{{info.main_contractor}}</td> 
        <td>{{info?.region}}</td> 
        <td>{{info.status}}</td> 
        <td>{{info?.sector}}</td> 

      </tr>
    </tbody>
  </table>

</div>
 </div>
</template>
<script>

export default {
  name: "Table",
  props:{
    apiData:Object,
  }
};
</script>

<style scoped lang="scss">
.projectsHeader{
  text-align: left;
  padding:0.9rem 0rem;
}
.table{
  margin:3rem 1em;
  border:1px solid red;

}
table{
  text-align: left;
  margin:auto;

  th {
    color:whitesmoke;
    background: #1c1c30;
    padding:0.7rem 1rem;

  }
  td{
     padding:0.5rem 1rem;
  }
  
}
.tableSection {
  width: 100%;
  overflow: auto;
}

.tableSection > table {
  margin-left: 22em;
}



.tableSection > table > * > tr > th:first-child,
.tableSection > table > * > tr > td:first-child{
  position: absolute;
  width: 20em;
  margin-left: -22em;
  text-align: left;
  background: white; 
}


tr:nth-child(even){
  background: skyblue;
}
//   .tableSection > table > * > tr:first-child :nth-child(even)  {
//    background:skyblue;
// }




.tableSection > table > * > tr > th:first-child {
    background: #1c1c30;
}

.tableSection > table > * > tr > th,
.tableSection > table > * > tr > td {
  /* Without this, if a cell wraps onto two lines, the first column
   * will look bad, and may need padding. */
  white-space: nowrap;
}
</style>
