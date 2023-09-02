<template>
    <section class="contact">
        <div class="contact__wrapper wrapper">
            <h1 class="contact__title">Связаться</h1>
            <h2 class="contact__subtitle">no email</h2>
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
import emailjs from '@emailjs/browser';

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
            }
        }
    },
    methods: {
        getName(obj){
            this.form.name = obj;
        },
        onSubmit(e){
            e.preventDefault();
            emailjs.send('service_35zotje', 'template_fru40xu', this.form, '_NOpZpbl_S67Mzb1o')
            .then((result) => {
                console.log('SUCCESS!', result.text);
            }, (error) => {
                console.log('FAILED...', error.text);
            });
        }
    },
    components: { InputText, TextArea, SendButton }
}
</script>

<style scoped lang="scss">
.contact {
    padding: 80px;
}

.contact__wrapper {
    background-color: #060606;
    position: relative;
    margin: 0px auto;
    padding: 80px 20px 20px;
    display: flex;
    flex-direction: column;
    gap: 6px;
    border-radius: 40px;
}

.contact__title {
    font-family: 'Neue Machina', Inter, Arial;
    font-size: 98px;
    line-height: 0.8;
    margin: 0;
}
.contact__subtitle {
    font-family: 'PP Migra Italic Extrabold Italic', serif;
    color: rgb(49,189,214);
    font-size: 90px;
    line-height: 0.8;
    text-align: center;
    padding: 0;
    margin: 0;
    margin: 0 0 40px;
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
    .contact {
        padding: 40px;
    }
    .contact__wrapper {
        padding: 16px;
        gap: 6px;
        margin: 0px;
    }

    .contact__title {
        font-size: 56px;
        padding: 40px 0 0;
    }

    .contact__subtitle {
        font-size: 50px;
        margin-bottom: 40px;

    }

    .form__info {
        grid-template-columns: 1fr;
        row-gap: 0px;
    }
}

@media screen and (max-width: 560px) {

    .contact {
        padding: 20px;
        margin-top: 20px;
    }

    .contact__wrapper {
        padding: 12px;
        gap: 6px;
        margin: 0px;
    }

    .contact__title {
        font-size: 46px;
        padding: 40px 0 0;
        margin: 0;
    }

    .contact__subtitle {
        font-size: 36px;
    }
}
</style>