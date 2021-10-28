<template>
<form action="">
    <Title>Регистрация</Title>
    <Description>Уже есть аккаунт?
        <Link>Войти
        </Link>
    </Description>
    <TextField :name="name.name" :placeholder="name.placeholder" :type="name.type" :setValue='setValue'></TextField>
    <TextField :name="mail.name" :placeholder="mail.placeholder" :type="mail.type" :setValue='setValue'></TextField>
    <TextField :name="phone.name" :placeholder="phone.placeholder" :type="phone.type" :setValue='setValue'></TextField>
    <DropDown :vars="language.vars" :name="language.name" :placeholder="language.placeholder" :type="language.type" :setValue='setValue'></DropDown>
    <Checkbox :type="checkRules.type" :setValue='setValue'>Принимаю
        <Link>условия</Link> использования</Checkbox>
    <Button :valid="valid" :send="send">Зарегистрироваться</Button>
</form>
</template>

<script>
import Title from './General/Title.vue'
import Description from './General/Description.vue'
import Link from './General/Link.vue'
import Button from './Controls/Button.vue'
import Checkbox from './Controls/Checkbox.vue'
import DropDown from './Controls/DropDown.vue'
import TextField from './Controls/TextField.vue'
export default {
    components: {
        Title,
        Description,
        Link,
        Button,
        Checkbox,
        DropDown,
        TextField
    },
    data() {
        return {
            name: {
                value: '',
                name: 'Имя',
                placeholder: 'Введите Ваше имя',
                type: 'name',
                valid: false
            },
            mail: {
                value: '',
                name: 'Email',
                placeholder: 'Введите Ваш email',
                type: 'mail',
                valid: false
            },
            phone: {
                value: '',
                name: 'Номер телефона',
                placeholder: 'Введите номер телефона',
                type: 'phone',
                valid: false
            },
            language: {
                value: '',
                name: 'Язык',
                placeholder: 'Язык',
                type: 'language',
                valid: false,
                vars: ['Русский', 'Английский', 'Китайский', 'Испанский']
            },
            checkRules: {
                type: 'checkRules',
                valid: false
            },
            valid: false
        }
    },
    methods: {
        setValue(data) {
            this.$set(this[data.type], 'value', data.value)
            this.$set(this[data.type], 'valid', data.valid)
            this.checkForValid()
        },
        checkForValid() {
            if (this.name.valid && this.mail.valid && this.phone.valid && this.language.valid && this.checkRules.valid) {
                this.valid = true
            } else {
                this.valid = false
            }
        },
        send() {

        }
    },
}
</script>

<style>
form {
    flex: 0 1 460px;
    padding: 40px 30px;
   box-sizing: border-box;
    background: #FFFFFF;
    box-shadow: 0px 12px 24px rgba(44, 39, 56, 0.02), 0px 32px 64px rgba(44, 39, 56, 0.04);
    border-radius: 24px;
}
</style>
