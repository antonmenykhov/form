<template>
<button :disabled="!valid" class="sendBtn" :class="{'active':valid}">
    <slot></slot>
</button>
</template>

<script>
export default {
    props: {
        valid: Boolean,
        send: Function,
    }
}
</script>

<style>
.sendBtn {
    background: #DBE2EA;
    box-shadow: 0px 2px 4px rgba(44, 39, 56, 0.08), 0px 4px 8px rgba(44, 39, 56, 0.08);
    border-radius: 6px;
    height: 56px;
    width: 100%;
    border: none;
    font-weight: 500;
    font-size: 16px;
    line-height: 21px;
    color: #B1B5BF
}
.sendBtn.active{
    background: #0880AE;
    color: #EBF4F8;
}
</style>
