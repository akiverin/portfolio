<template>
    <textarea class="textarea" @input="emitInput" v-model="value" :placeholder="placeholder" :required="required" :name="name" :id="id"></textarea>
    <p v-if="this.error" class="error error--disable">{{ this.error }}</p>
</template>

<script>
export default {
    name: 'TextAreaComponent',
    props: {
        modelValue: {
            type: String,
            required: true
        },
        placeholder: {
            type: String,
            default: '',
        },
        required: {
            type: String,
            default: 'false',
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
            value: this.modelValue,
            error: '',
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
    .message {
        width: 100%;
    }
    .textarea {
        display: flex;
        font-family: 'PP Neue Machina Regular';
        min-height: 64px;
        resize: vertical;
        height: 200px;
        color: #f1f1f1;
        background-color: transparent;
        border: 1px solid rgba(241,241,241,.35);
        border-radius: 12px;
        margin: 10px;
        padding: 14px 24px;
        font-size: 20px;
        line-height: 1.5;
        transition: all .1s;
        outline: 1px;
        &:hover {
            border-color: rgba(241,241,241,.6);
        }
        &:active {
            border-color: #f1f1f1;
        }
    }

    @media screen and (max-width: 560px){
        .textarea {
            font-size: 18px;
        }
    }
</style>