<template>
  <div class="opcionesContainer">
    <ul>
        <li>1</li>
        <li>2</li>
        <li>3</li>
        <li>4</li>
    </ul>

  </div>
</template>

<script>
export default {

}
</script>

<style>
ul{
    list-style-type: none;
}
li{
    display: flex;
    border: 1px solid black;
    border-radius: 5px;
    margin-bottom: 10px;
    width: 250px ;
    background: white;
    cursor: pointer;

    
}
li:hover{
    background: rgba(0, 0, 0, 0.05);
}
.opcionesContainer{
    display: flex;
    justify-content: center;
}

</style>