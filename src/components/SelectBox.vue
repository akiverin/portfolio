<template>
    <div class="search-bar">
        <label :for="id" class="search-bar__title">{{ title }}</label>
        <select :name="title" :id="id" v-model="selected" @change="handleSelect">
            <option v-for="item in content" :key="item.value" :value="item.value">{{ item.name }}</option>
        </select>
    </div>
</template>

<script>
export default {
    name: "SelectBox",
    props: {
        onSelect: {
            type: Function,
            required: true,
        },
        title: {
            type: String,
            required: true,
        },
        id: {
            type: String,
            required: true,
        },
        content: {
            type: Array,
            required: true,
        },
    },
    data() {
        return {
            selected: this.content.length > 0 ? this.content[0].value : null,
        };
    },
    watch: {
        content: {
            immediate: true,
            handler(newContent) {
                if (newContent.length && (!this.selected || !newContent.some(item => item.value === this.selected))) {
                    this.selected = newContent[0].value;
                }
            },
        },
    },
    methods: {
        handleSelect() {
            console.log(this.selected)
            this.$emit('select', this.selected);
        },
    },
};
</script>

<style scoped>
.search-bar {
    margin-bottom: 20px;
    display: flex;
    flex-direction: column;
}

.search-bar__title {
    font-size: 1rem;
    margin-bottom: 5px;
    color: #333;
    font-weight: 300;
    text-align: left;
}

select {
    padding: 10px;
    width: 100%;
    border: 1px solid #ccc;
    border-radius: 5px;
    padding: 10px;
    width: 100%;
    border: 1px solid #ccc;
    border-radius: 10px;
    font-size: 16px;
    font-size: 16px;
    background-color: #fff;
    appearance: none;
    cursor: pointer;
    transition: border-color 0.3s;
}

select:focus {
    outline: none;
    border-color: #007BFF;
}

select option {
    padding: 10px;
}
</style>
