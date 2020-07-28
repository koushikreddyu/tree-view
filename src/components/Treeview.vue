<template>
    <div>
        <div
            @click="nodeClicked"
            :style="{'margin-left': `${depth*20}px`}"
        >{{node.name}}</div>
        <div v-if="expanded">
            <Treeview 
                v-for="child in node.children"
                :key="child.name"
                :node="child"
                :depth="depth+1"
            />
        </div>
    </div>
</template>

<script>
export default {
    name:"Treeview",
    props: {
        node: Object,
        depth: {
            type: Number,
            default: 0
        }
    },
    data() {
        return {
            expanded: false
        }
    },
    methods: {
        nodeClicked() {
            this.expanded = !this.expanded
        }
    }
}
</script>