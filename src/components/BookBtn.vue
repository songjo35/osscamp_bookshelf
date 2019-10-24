<template>
    <el-tooltip class="item" effect="dark" :content="bookInfo.titleName" placement="bottom">
        <el-button @click="bookClicked" :type="colorType" v-bind:style="bookStyle" class="book">
            <p class="titleText">
                {{this.bookInfo.titleName}}
            </p>
        </el-button>
    </el-tooltip>
</template>

<script>
    export default {
        name: 'BookBtn',
        props: ['bookInfo'],
        mounted() {
            this.colorType = this.colorList[Math.floor(this.bookInfo.bookColor % 5)];
            console.log(this.myColor);
        },
        data() {
            return {
                colorList: [
                    'primary',
                    'success',
                    'info',
                    'warning',
                    'danger'
                ],
                colorType: "primary",
                bookStyle: {
                    width: this.bookInfo.width + 'px',
                    height: this.bookInfo.height + 'px',
                }
            }
        },
        methods: {
            bookClicked() {
                console.log(":aaaaaaaaaaasdf");
                this.$emit('bookClicked', this.bookInfo.floor, this.bookInfo.id);
            }
        }
    }
</script>

<style scoped>
    .book {
        overflow: hidden;
        margin: 0px 2px 0px 2px;
        align-items: center;
        padding: 4px 0px 0px 0px;
    }

    .titleText {
        writing-mode: tb-rl;
        margin: 0 auto;
    }
</style>