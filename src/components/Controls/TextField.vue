<template>
<div class="textField">
    <Label>{{name}}</Label>
    <input v-model="componentValue" type="text" :placeholder="placeholder">
    <ValidationMessage v-if="!valid">Введено не корректное значение</ValidationMessage>
</div>
</template>

<script>
import Label from '../General/Label.vue'
import ValidationMessage from '../General/ValidationMessage.vue'

export default {
    props: {
        name: String,
        type: String,
        placeholder: String,
        value: String,
        setValue: Function
    },
    data() {
        return {
            componentValue: '',
            valid: true,
            pattern: {
                // eslint-disable-next-line
                name: /^[А-Яа-яA-Za-z]{1,}[А-Яа-яA-Za-z\s\-]+$/,
                // eslint-disable-next-line
                mail: /^([a-z0-9_-]+\.)*[a-z0-9_-]+@[a-z0-9_-]+(\.[a-z0-9_-]+)*\.[a-z]{2,6}$/,
                // eslint-disable-next-line
                phone: /^((8|\+7)[\- ]?)?(\(?\d{3}\)?[\- ]?)?[\d\- ]{7,10}$/

            }
        }
    },
    components: {
        Label,
        ValidationMessage
    },
    watch: {
        componentValue: function () {

            if (this.pattern[this.type].test(this.componentValue)) {
                this.valid = true
                this.setValue({
                    type: this.type,
                    value: this.componentValue,
                    valid: true
                })
            } else {
                this.valid = false
                this.setValue({
                    type: this.type,
                    valid: false
                })
            }
        }
    }
}
</script>

<style>
.textField {
    display: flex;
    flex-direction: column;
    align-items: flex-start;
    min-height: 114px;
}

input[type="text"], select {
    background: #FFFFFF;
    border: 1px solid #DBE2EA;
    box-sizing: border-box;
    box-shadow: 0px 4px 8px rgba(44, 39, 56, 0.04);
    border-radius: 6px;
    width: 100%;
    color: #2C2738;
    font-size: 16px;
    line-height: 21px;
    padding: 16px 16px 15px;

}

input[type="text"]::placeholder, select::placeholder {
    color: #7C9CBF
}

input[type="text"]:focus, select:focus{
  
    outline: 2px solid #0880AE;
}
</style>
