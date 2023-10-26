<template>
    <div>
        <label
            >Name:
            <input class="name" ref="inpName" type="text" v-model="nameVal" />
        </label>
    </div>
    <div>
        <label
            >Age:
            <input class="age" ref="inpAge" type="number" v-model="ageVal" />
        </label>
    </div>
</template>
<script>
export default {
    name: 'EnterData',

    props: {
        name: {
            type: String,
        },
        age: {
            type: Number,
        },
        nameModifiers: { default: () => ({}) },
        ageModifiers: { default: () => ({}) },
    },

    computed: {
        nameVal: {
            get() {
                return this.name
            },
            set(val) {
                if (this.nameModifiers.checkEmpty) this.setNameBGColor(val)

                this.$emit('update:name', val)
            },
        },
        ageVal: {
            get() {
                return this.age
            },
            set(val) {
                if (this.ageModifiers.check18) this.setAgeBGColor(val)
                this.$emit('update:age', val)
            },
        },
    },

    methods: {
        setNameBGColor(val) {
            if (!val) this.$refs.inpName.style.backgroundColor = 'red'
            else this.$refs.inpName.style.backgroundColor = 'transparent'
        },
        setAgeBGColor(val) {
            if (!val) this.$refs.inpAge.style.backgroundColor = 'transparent'
            else if (val < 18) this.$refs.inpAge.style.backgroundColor = 'red'
            else this.$refs.inpAge.style.backgroundColor = 'green'
        },
    },
}
</script>
<style lang="scss" scoped>
.name {
    background-color: red;
}
.age {
    margin-top: 10px;
}
</style>
