<template>
    <div class="home">
        <el-menu class="el-menu-demo" mode="horizontal">
            <el-menu-item index="1" class="app-title">나만의 책장</el-menu-item>
            <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">Orders</a></el-menu-item>
        </el-menu>

        <div class="shelf-frame">
            <div class="book-container">
                <BookBtn v-for="(book, index) in bookList2" :key="index" :book-info="book" @bookClicked="showInfo">
                </BookBtn>
            </div>
            <div class="book-container">
                <BookBtn v-for="(book, index) in bookList1" :key="index" :book-info="book" v-on:bookClicked="showInfo">
                </BookBtn>
            </div>
            <div class="book-container">
                <BookBtn v-for="(book, index) in bookList0" :key="index" :book-info="book" v-on:bookClicked="showInfo">
                </BookBtn>
            </div>
        </div>

        <!-- #1 : BookInfoModal window -->
        <el-dialog title="Tips" :visible.sync="bookInfoModalShow" width="30%">
            <span>This is a message</span>
            <span slot="footer" class="dialog-footer">
                <el-button @click="bookInfoModalShow = false">Cancel</el-button>
                <el-button type="primary" @click="bookInfoModalShow = false">Confirm</el-button>
            </span>
        </el-dialog>

        <!-- #1 : Button troggle motal -->
        <el-button type="primary" icon="el-icon-plus" circle class="add-btn" @click="addBookBtnClick"></el-button>
        <!-- #2 : Add Modal Window -->
        <el-dialog title="책 추가" :visible.sync="addBookModalShow" width="30%" class="add-book-modal">
            <el-form :model="addBookForm">
                <el-form-item label="책 제목 검색 및 등록" label-width="120px">
                    <el-input v-model="addBookForm.titleName" aria-autocomplete="off"></el-input>
                </el-form-item>
                <el-form-item label="책 색상" label-width="120px">
                    <el-select v-model="addBookForm.color" placeholder="Select">
                        <el-option v-for="item in bookColorOptions" :key="item.value" :label="item.label" :value="item.value">
                        </el-option>
                    </el-select>
                </el-form-item>
                <el-form-item label="책 높이" label-width="120px">
                    <el-slider v-model="addBookForm.height" max="180" min="80"></el-slider>
                </el-form-item>
                <el-form-item label="책 너비">
                    <el-slider v-model="addBookForm.width" max="100" min="50"></el-slider>
                </el-form-item>
            </el-form>
        </el-dialog>
    </div>

</template>

<script>
    import HelloWorld from '@/components/HelloWorld.vue'
    import BookBtn from '@/components/BookBtn.vue'
    import BookInfo from '@/components/BookInfo.vue'
    import AddBookPopup from '@/components/AddBookPopup.vue'

    export default {
        name: 'home',
        components: {
            HelloWorld,
            BookBtn
        },
        methods: {
            showInfo(floor, id) {
                this.bookInfoModalShow = true;
            },
            addBookBtnClick() {
                this.addBookModalShow = true;
            },
            pushBookData(floor) {
                const book = {
                    titleName: '',
                    color: 0,
                    floor: floor,
                    id: getBL(floor)[getBL(floor).length - 1].id + 1,
                    width: 50,
                    height: 80,
                    comment: '',
                    phrases: [],
                    star: 3
                }
            },
            getBL(floor) {
                switch (floor) {
                    case 0:
                        return this.bookList0;
                    case 1:
                        return this.bookList1;
                    case 2:
                        return this.bookList2;
                }
            }
        },
        data() {
            return {
                bookInfoModalShow: false,
                addBookModalShow: false,
                bookColorOptions: [{
                    value: 0,
                    label: '파랑색'
                }, {
                    value: 1,
                    label: '초록색'
                }, {
                    value: 2,
                    label: '회색'
                }, {
                    value: 3,
                    label: '주황색'
                }, {
                    value: 4,
                    label: '빨간색'
                }],
                addBookForm: {
                    titleName: '',
                    color: 0,
                    width: 50,
                    height: 80,
                    comment: '',
                    phrases: [],
                    star: 3
                },
                bookList2: [{
                        floor: 2,
                        id: 0,
                        width: 100,
                        height: 120,
                        bookColor: 0,
                        titleName: "1984",
                    },
                    {
                        floor: 2,
                        id: 1,
                        width: 50,
                        height: 60,
                        bookColor: 3,
                        titleName: "노르웨이의 숲",
                    },
                    {
                        floor: 2,
                        id: 2,
                        width: 70,
                        height: 80,
                        bookColor: 1,
                        titleName: "칼의 노래",
                    },
                    {
                        floor: 2,
                        id: 3,
                        width: 60,
                        height: 100,
                        bookColor: 3,
                        titleName: "자바 스크립트 완벽 가이드",
                    },
                    {
                        floor: 2,
                        id: 4,
                        width: 50,
                        height: 90,
                        bookColor: 4,
                        titleName: "동물농장",
                    }
                ],
                bookList1: [{
                        floor: 1,
                        id: 0,
                        width: 100,
                        height: 120,
                        bookColor: 0,
                        titleName: "1984",
                    },
                    {
                        floor: 1,
                        id: 1,
                        width: 50,
                        height: 60,
                        bookColor: 3,
                        titleName: "노르웨이의 숲",
                    },
                    {
                        floor: 1,
                        id: 2,
                        width: 70,
                        height: 80,
                        bookColor: 1,
                        titleName: "칼의 노래",
                    },
                    {
                        floor: 1,
                        id: 3,
                        width: 60,
                        height: 100,
                        bookColor: 3,
                        titleName: "자바 스크립트 완벽 가이드",
                    },
                    {
                        floor: 1,
                        id: 4,
                        width: 50,
                        height: 90,
                        bookColor: 4,
                        titleName: "동물농장",
                    }
                ],
                bookList0: [{
                        floor: 0,
                        id: 0,
                        width: 100,
                        height: 120,
                        bookColor: 0,
                        titleName: "1984",
                    },
                    {
                        floor: 0,
                        id: 1,
                        width: 50,
                        height: 60,
                        bookColor: 3,
                        titleName: "노르웨이의 숲",
                    },
                    {
                        floor: 0,
                        id: 2,
                        width: 70,
                        height: 80,
                        bookColor: 1,
                        titleName: "칼의 노래",
                    },
                    {
                        floor: 0,
                        id: 3,
                        width: 60,
                        height: 100,
                        bookColor: 3,
                        titleName: "자바 스크립트 완벽 가이드",
                    },
                    {
                        floor: 0,
                        id: 4,
                        width: 50,
                        height: 90,
                        bookColor: 4,
                        titleName: "동물농장",
                    }
                ]
            }
        },

    }
</script>

<style>
    .add-book-modal {}

    .shelf-frame {
        display: flex;
        flex-direction: column;
        background-color: #d3dce6;
        left: 50%;
        top: 50%;
        position: absolute;
        width: 500px;
        height: 800px;
        transform: translate(-50%, -46%);
        border-radius: 10px;
        box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04)
    }

    .add-btn {
        position: absolute;
        top: 25%;
        left: 65%;
    }

    .book-container {
        flex: 1 1 20px;
        display: flex;
        align-items: flex-end;
        background-color: #ebf0f7;
        border-radius: 5px;
        margin: 10px;
    }

    .app-title {
        font-size: 20px;
        font-weight: bold;
    }

    .bg-purple {
        background: #d3dce6;
    }

    .bg-purple-dark {
        background: #ebf0f7;
    }

    .bg-purple-light {
        background: #e5e9f2;
    }
</style>