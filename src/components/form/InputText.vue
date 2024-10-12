<template>
    <input 
        class="input" 
        v-model="value" 
        @input="emitInput"
        :type="type" 
        :placeholder="placeholder" 
        :required="required" 
        :name="name" 
        :id="id"
    />
</template>

<script>
export default {
    name: 'InputTextComponent',
    props: {
        modelValue: {
            type: String,
            required: true
        },
        msg: {
            type: String,
            default: '',
        },
        required: {
            type: String,
            default: 'false',
        },
        placeholder: {
            type: String,
            default: '',
        },
        type: {
            type: String,
            default: '',
        },
        name: {
            type: String,
            default: '',
        },
        id: {
            type: String,
            default: '',
        },
    },
    data() {
        return {
            value: this.modelValue
        };
    },
    methods: {
        emitInput() {
            this.$emit('update:modelValue', this.value);
        },
    }
}
</script>

<style scoped lang="scss">
    .input {
        font-family: 'PP Neue Machina Regular';
        min-height: 64px;
        color: #f1f1f1;
        background-color: transparent;
        border: 1px solid rgba(241,241,241,.35);
        border-radius: 12px;
        margin: 10px;
        padding: 0 0 0 18px;
        font-size: 20px;
        line-height: 1.5;
        transition: all .45s;
        outline: 1px;
        &:hover {
            border-color: rgba(241,241,241,.6);
        }
        &:active {
            border-color: #f1f1f1;
        }
        &::placeholder {
        }
    }

    @media screen and (max-width: 560px){
        .input {
            font-size: 18px;
        }
    }
</style>