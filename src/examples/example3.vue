<template>

    <div id="sidebar">
      <Slider :title="heightSliderName" :min="1" max="30" :step="1" :val="heightSliderValue" @update="updateValue"></Slider>
      <Slider :title="widthSliderName" :min="1" max="30" :step="1" :val="widthSliderValue" @update="updateValue"></Slider>
      <Slider :title="verticalRotationSliderName" :min="1" max="30" :step="1" :val="verticalRotationValue" @update="updateValue"></Slider>
      <Slider :title="horizontalRotationSliderName" :min="1" max="15" :step="1" :val="horizontalRotationValue" @update="updateValue"></Slider>
      <Dropdown :title="shapeTypeDropdownName" :options="shapeTypeDropdownOptions":val="shapeIndex" @update="updateValue"></Dropdown>
    </div>
  
    <div id="viewer">
        <GeometryView :data="inputs" :path="path" @updateMetadata="receiveMetadata"></GeometryView>
    </div>
  </template>
  
  <script setup>
  import { ref, onBeforeMount, computed } from "vue"
  import GeometryView from "../components/GeometryView.vue"
  import Slider from '../components/Slider.vue'
  import Dropdown from "../components/Dropdown.vue"
  import Toggle from "../components/Toggle.vue"
  
  //define path to grasshopper script
  import def from "../assets/wall_start.gh"
  const path = def
  
  //define input names and values
  const heightSliderName = ref("Height")
  const heightSliderValue = ref(50)

  const widthSliderName = ref("Width")
  const widthSliderValue = ref(20)
  
  const shapeTypeDropdownName = ref("ShapeType")
  const shapeIndex = ref(0)
  const shapeTypeDropdownOptions = ref([{label:"Standard", value:0}, {label:"Concave", value:1}, {label:"Convex", value:2}])

  const verticalRotationSliderName = ref("VerticalRotation")
  const verticalRotationValue = ref(10)

  const horizontalRotationSliderName = ref("HorizontalRotation")
  const horizontalRotationValue = ref(10)
  
  let metadata = ref([])

  
  //define inputs
  let inputs = ref({
    [heightSliderName.value]: heightSliderValue.value ,
    [widthSliderName.value] : widthSliderValue.value ,
    [verticalRotationSliderName.value] : verticalRotationValue.value,
    [horizontalRotationSliderName.value] : horizontalRotationValue.value,
    [shapeTypeDropdownName.value] : shapeIndex.value
  });
  
  function updateValue(newValue, parameterName) {
    // Iterate over the inputs array
    for (const [key, value] of Object.entries(inputs.value)) {
      if (key == parameterName){
          inputs.value[key] = newValue
          console.log(parameterName + ':' + newValue)
      }
    }
  }
  function receiveMetadata(newValue) {
    console.log(newValue)
    metadata.value = newValue
  }

  
  </script>
  
  <style scoped>
  
  #sidebar {
    width: 310px;
    padding: 20px;
    flex-shrink: 0; 
  }
  
  #viewer { 
    width: 100%;
    margin: 20px
  }
  
  </style>
