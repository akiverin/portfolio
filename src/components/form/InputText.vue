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
            type: Text,
            default: '',
        },
        required: {
            type: Boolean,
            default: false,
        },
        placeholder: {
            type: Text,
            default: '',
        },
        type: {
            type: Text,
            default: '',
        },
        name: {
            type: Text,
            default: '',
        },
        id: {
            type: Text,
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
        padding: 0 18px;
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
</style>