<script lang="ts">
 import { Socket, Output, Component, Node, NodeEditor } from "rete";
 import NumControl from "./NumControl.vue";

 export default class NumComponent extends Component {
     numSocket: Socket;

     constructor(numSocket: Socket){
         super("Number");
         this.numSocket = numSocket;
     }

     builder(node: Node) {
         var out1 = new Output('num', "Number", this.numSocket);

         return node.addControl(new NumControl(this.editor, 'num')).addOutput(out1);
     }

     worker(node: Node, inputs, outputs) {
         outputs['num'] = node.data.num;
     }
 }
</script>
