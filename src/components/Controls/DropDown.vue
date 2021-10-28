<template>
<div class="select-box">
    <Label>{{name}}</Label>
    <button @click="toggleVars" class="select">{{componentValue}}</button>
    <div v-if="showVars" @click="showVars=false" class="selectVars">
        <button class="option" @click="componentValue=item" v-for="item,i in vars" :key="i">{{item}} </button>
    </div>
    <div v-show="!componentValue" class="placeholder">{{placeholder}}</div>
</div>
</template>

<script>
import Label from '../General/Label.vue'
export default {
    props: {
        name: String,
        type: String,
        placeholder: String,
        value: String,
        setValue: Function,
        vars: Array
    },
    data() {
        return {
            componentValue: '',
            showVars: false
        }
    },
    components: {
        Label,
    },
    methods: {
        toggleVars(e) {
            e.preventDefault()
            this.showVars = !this.showVars
        }
    },
    watch: {
        componentValue: function() {
            this.setValue({
                    type: this.type,
                    value: this.componentValue,
                    valid: true
                }
            )
        }
    }
}
</script>

<style>
.selectVars {
    background: #FFFFFF;
    border: 1px solid #DBE2EA;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04), 0px 20px 20px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    position: absolute;
    width: 100%;
    top: 87px;
    display: flex;
    flex-direction: column;
    overflow: hidden;
    z-index: 3;
}

.option {
    border: none;
    border-radius: 0;
    background: white;
    font-size: 16px;
    line-height: 21px;
    padding: 12px 15px 11px;
    text-align: left;
    outline: none;
    color: #756F86
}

.option:focus,
.option:hover {
    outline: none;
    background: #EBF4F8;
    ;
}

.select-box {
    position: relative;
    min-height: 114px;
    display: flex;
    flex-direction: column;
    align-items: flex-start;
}

.select {
    background: #FFFFFF;
    border: 1px solid #DBE2EA;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    width: 100%;
    color: #2C2738;
    font-size: 16px;
    line-height: 21px;
    padding: 16px;
    min-height: 52px;
    text-align: left;
    position: relative;
}

.select::before {
    position: absolute;
    content: '';
    background: url('/img/Mask.png') no-repeat center center / contain;
    height: 20px;
    width: 20px;
    z-index: 200;
    top: 16px;
    right: 16px;
}

.placeholder {
    position: absolute;
    top: 29px;
    padding: 16px;
    color: #7C9CBF
}

option {
    display: none;
}

button:focus {
    outline: 2px solid #0880AE;
}
</style>
