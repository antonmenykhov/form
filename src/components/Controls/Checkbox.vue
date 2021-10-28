<template>
<div class="checkBox-box">
    <Label></Label>
    <input type="checkbox" id="checkbox1" name="checkbox" v-model="componentValue">
    <label class="checkbox" for="checkbox1">
        <p class="rules"><slot></slot></p>
        
    </label>
</div>
</template>

<script>
import Label from '../General/Label.vue'
export default {
    props:{
        setValue: Function,
        type: String
    },
    components: { Label },
    data() {
        return {
            componentValue: false
        }
    },
    watch: {
        componentValue: function () {
            this.setValue({
                type: this.type,

                valid: this.componentValue
            })
        }
    }
}
</script>

<style>
.rules{
    font-size: 16px;
    line-height: 21px;
    font-weight: 500;
    margin-left: 7px;
    color: #756F86;
    flex:1;
    text-align: left;
}
.checkBox-box {
    display: flex;
    justify-content: flex-start;
   margin-bottom: 39px;
}

input[type="checkbox"] {
    opacity: 0;
    z-index: -2;
    position: absolute;
}

input[type="checkbox"]+label {
    display: inline-flex;
    align-items: center;
    user-select: none;
    position: relative;
}

input[type="checkbox"]+label::before {
    content: '';

    border: 1px solid #DBE2EA;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 4px;
    height: 28px;
    width: 28px;

}

input[type="checkbox"]:checked+label::before {
    border: 2px solid #0880AE;
}

input[type="checkbox"]+label::after {
    opacity: 0;
    content: '';
    height: 16px;
    width: 16px;
    position: absolute;
    left: 6px;
    top: 6px;
    background: url('/img/Accent.png') no-repeat center center / contain;
    transition: all .1s;
}

input[type="checkbox"]:checked+label::after {
    opacity: 1;
}



input[type="checkbox"]:focus+label::before {
    border: 2px solid #0880AE;
}
</style>
