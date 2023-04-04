<script lang="ts">
 import { Socket, Input, Output, Component, Node, NodeEditor } from "rete";
 import NumControl from "./NumControl.vue";

 export default class AddComponent extends Component {
     numSocket: Socket;

     constructor(numSocket: Socket){
         super("Add");
         this.numSocket = numSocket;
     }

     builder(node: Node) {
         var inp1 = new Input('num',"Number", this.numSocket);
         var inp2 = new Input('num2', "Number2", this.numSocket);
         var out = new Output('num', "Number", this.numSocket);

         inp1.addControl(new NumControl(this.editor, 'num'))
         inp2.addControl(new NumControl(this.editor, 'num2'))

         return node
             .addInput(inp1)
             .addInput(inp2)
             .addControl(new NumControl(this.editor, 'preview', true))
             .addOutput(out);
     }

     worker(node: Node, inputs, outputs) {
         var n1 = inputs['num'].length?inputs['num'][0]:node.data.num1;
         var n2 = inputs['num2'].length?inputs['num2'][0]:node.data.num2;
         var sum = n1 + n2;

         this.editor.nodes.find(n => n.id == node.id).controls.get('preview').setValue(sum);
         outputs['num'] = sum;
     }
 }
</script>
