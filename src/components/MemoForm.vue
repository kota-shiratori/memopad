<template>
    <div><input type="text" v-model="title" placeholder="タイトル"></div>
    <div><textarea v-model="content" placeholder="内容"></textarea></div>
    <div class="center">
        <button class="save-button" @click="save">保存</button>
        <button class="delete-button" @click="remove" v-if="memo.id">削除</button>
    </div>
</template>

<script>
export default {
    name: 'MemoForm',
    props: [
        'memo'
    ],
    data() {
        return {
            title: this.memo?.title || '',
            content: this.memo?.content || '',
        }
    },
    methods: {
        save() {

            if (!this.title.trim() || !this.content.trim()) {
                alert('タイトルと内容は必須です。');
                return;
            }

            let memo = {
                title: this.title,
                content: this.content
            }

            if (this.memo.id) {
                memo.id = this.memo.id
            }

            this.$store.commit('save', memo)
            this.$router.push('/')
        },
        remove() {
            this.$store.commit('delete', this.memo.id)
            this.$router.push('/')
        }
    }
}
</script>

<style scoped>
div {
    margin-bottom: 10px;
}

input[type=text] {
    width: 100%;
    padding: 1em;
    box-sizing: border-box;
    border: solid 2px #42b983;
}

textarea {
    width: 100%;
    height: 30em;
    padding: 1em;
    box-sizing: border-box;
    border: solid 2px #42b983;
}

button {
    width: 5em;
    margin: 3px;
}

.center {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
}

.save-button,
.delete-button {
    background-color: #42b983;
    border-radius: 10px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 1em;
    color: #fff;
    border: none;
    cursor: pointer;
    font-weight: bold;
}

.save-button {
    background-color: #42b983;
}

.delete-button {
    background-color: #f08080;
}
</style>