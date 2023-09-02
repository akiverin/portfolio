<template>
    <section class="contact">
        <div class="contact__wrapper">
            <h1 class="contact__title">Связаться</h1>
            <form class="contact__form form" @submit="onSubmit">
                <div class="form__info">
                    <InputText v-model="form.name" type="text" required="true" placeholder="Ваше имя" name="name" id="nameInput"/>
                    <InputText v-model="form.email" type="email" required="true" placeholder="Email" name="email" id="emailInput"/>
                </div>
                <TextArea v-model="form.msg" required="true" placeholder="Ваше сообщение" minlength="12" name="message" id="messageInput"></TextArea>
                <SendButton>Отправить</SendButton>
            </form>
        </div>
    </section>
</template>

<script>
import InputText from './form/InputText.vue';
import SendButton from './form/SendButton.vue';
import TextArea from './form/TextArea.vue';

export default {
    name: "ContactSection",
    data(){
        return {
            form: {
                name: '',
                email: '',
                msg: '',
                error: '',
                valid: false,
            }
        }
    },
    methods: {
        getName(obj){
            this.form.name = obj;
        },
        onSubmit(e){
            e.preventDefault();
            console.log(this.form);
        }
    },
    components: { InputText, TextArea, SendButton }
}
</script>

<style scoped lang="scss">

.contact__wrapper {
    background-color: #060606;
    padding: 20px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    border-radius: 40px;
    margin: 80px;
}

.contact__title {
    font-family: 'Neue Machina', Inter, Arial;
    font-size: 98px;
}

.form {
    display: flex;
    flex-direction: column;
}
.form__info {
    display: grid;
    grid-template-columns: 1fr 1fr;
    column-gap: 10px;
    width: 100%;
}

@media screen and (max-width: 856px) {
    .contact__wrapper {
        padding: 16px;
        gap: 6px;
        margin: 40px;
    }

    .form__info {
        grid-template-columns: 1fr;
        row-gap: 0px;
    }
}

@media screen and (max-width: 560px) {
    .contact__wrapper {
        padding: 12px;
        gap: 6px;
        margin: 20px;
    }
}
</style>