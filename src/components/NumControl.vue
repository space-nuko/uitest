<script lang="ts">
import { Socket, NodeEditor, Control, Output, Input, Component, Engine } from "rete";
 import VueNumControl from './VueNumControl.vue'

 export default class NumControl extends Control {
     constructor(emitter: any, key: string, readonly: boolean) {
         super(key);
         this.component = VueNumControl;
         this.props = { emitter, ikey: key, readonly };
     }

     setValue(val) {
         this.vueContext.value = val;
     }
 }
</script>
