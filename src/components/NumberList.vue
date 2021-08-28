<template>
  <div id="number-list">
    <h1>Unordered List from 3 to 103</h1>
    <div v-for="number in divisibleNumbers" :key="number">
        <h3>{{ number }}</h3>
    </div>
  </div>
</template>

<script>

export default ({
    name: 'NumberList',
    data() {
        return {
            divisibleNumbers: [],
        }
    },
    created(){
        this.createUnorderedList(3, 103);
    },
    methods: {
        createUnorderedList(start, end) {
            Array(end - start + 1)
                    .fill()
                    .map((_, idx) => start + idx)
                    .sort(function(){
                        return 0.5 - Math.random()
                    }).forEach(this.evaluateNumbers);
        },
        evaluateNumbers(value){
            if (value % 5 == 0 && value % 3 == 0) {
                this.divisibleNumbers.push(value + " - three and five");
            } else if (value % 5 == 0) {
                this.divisibleNumbers.push(value + " - five");
            } else if (value % 3 == 0) {
                this.divisibleNumbers.push(value + " - three");
            }
        }
    }
})
</script>
