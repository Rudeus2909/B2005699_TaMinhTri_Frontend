<template>
    <div class="page">
        <h4>Thêm liên hệ</h4>
        <ContactForm :contact="contact" @add:contact="addContact" />
        <p>{{ message }}</p>
    </div>
</template>

<script>
import ContactForm from '../components/ContactForm.vue';
import ContactService from "@/services/contact.service";

export default {
    components: {
        ContactForm,
    },
    data() {
        return {
            contact: {
                name: '',
                address: '',
                email: '',
                phone: '',
                favorite: false,
            },
            message: "",
        }
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được thêm thành công";
            } catch (error) {
                console.log(error);
            }
        },
    },

}
</script>