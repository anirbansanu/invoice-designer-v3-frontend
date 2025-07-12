<template>
  <div class="designer">
    <aside class="p-3 bg-light border-end" style="width: 260px;">
      <h5 class="mb-3">Components</h5>
      <button class="btn btn-outline-primary btn-sm mb-2 w-100" @click="addText">Add Text</button>
      <button class="btn btn-outline-primary btn-sm mb-2 w-100" @click="addBox">Add Box</button>
      <button class="btn btn-outline-primary btn-sm mb-2 w-100" @click="addQR">Add QR</button>
      <button class="btn btn-outline-primary btn-sm mb-2 w-100" @click="addBarcode">Add Barcode</button>
      <button class="btn btn-outline-primary btn-sm mb-2 w-100" @click="uploadImage">Upload Image</button>
      <button class="btn btn-outline-primary btn-sm mb-4 w-100" @click="addTable">Add Table</button>

      <h5 class="mb-3">Utilities</h5>
      <button class="btn btn-success btn-sm mb-2 w-100" @click="save">Save</button>
      <button class="btn btn-warning btn-sm mb-2 w-100" @click="load">Load</button>
      <button class="btn btn-secondary btn-sm mb-2 w-100" @click="undo">Undo</button>
      <button class="btn btn-secondary btn-sm mb-2 w-100" @click="redo">Redo</button>
      <button class="btn btn-danger btn-sm w-100" @click="clear">Clear</button>
    </aside>

    <div class="canvas-container">
      <canvas id="canvas" width="800" height="1000" style="border: 1px solid #000;"></canvas>
    </div>
  </div>
</template>

<script setup>
import { onMounted } from 'vue'
import { fabric } from 'fabric'
import axios from 'axios'
import hotkeys from 'hotkeys-js'

let canvas;

onMounted(() => {
  canvas = new fabric.Canvas('canvas');
  hotkeys('ctrl+s', (e) => { e.preventDefault(); save() });
  hotkeys('ctrl+z', (e) => { e.preventDefault(); undo() });
})

function addText() {
  canvas.add(new fabric.Textbox('Text', { left: 100, top: 100, fontSize: 18 }))
}
function addBox() {
  canvas.add(new fabric.Rect({ left: 150, top: 150, width: 200, height: 100, stroke: 'black', fill: 'transparent' }))
}
function addQR() {
  canvas.add(new fabric.Text('QR Placeholder', { left: 300, top: 200, fontSize: 16 }))
}
function addBarcode() {
  canvas.add(new fabric.Text('Barcode Placeholder', { left: 350, top: 250, fontSize: 16 }))
}
function addTable() {
  canvas.add(new fabric.Text('Table Placeholder', { left: 200, top: 300, fontSize: 14 }))
}
function uploadImage() {
  alert("Image upload placeholder. Connect to Laravel API.");
}
function clear() {
  canvas.clear()
}
function undo() {
  // Placeholder for undo
  alert("Undo triggered")
}
function redo() {
  // Placeholder for redo
  alert("Redo triggered")
}
function save() {
  const json = canvas.toJSON()
  const components = json.objects.map(obj => ({
    type: obj.type,
    label: obj.text || obj.type,
    position: { x: obj.left, y: obj.top },
    font: { size: obj.fontSize || 12 }
  }))
  axios.post('http://localhost:8000/api/templates', {
    business_id: 1,
    name: 'Pro V3 Invoice',
    type: 'invoice',
    version: 3,
    is_active: true,
    components
  }).then(() => alert("Saved"))
}
function load() {
  axios.get('http://localhost:8000/api/templates').then(res => {
    const template = res.data[0]
    clear()
    template.components.forEach(c => {
      if (c.type === 'text') {
        canvas.add(new fabric.Textbox(c.label, { left: c.position.x, top: c.position.y, fontSize: c.font.size }))
      }
    })
  })
}
</script>

<style scoped>
.designer { display: flex; width: 100%; }
.sidebar { width: 220px; padding: 10px; background: #f4f4f4; display: flex; flex-direction: column; gap: 8px; }
.canvas-container { flex: 1; display: flex; justify-content: center; align-items: center; }
</style>