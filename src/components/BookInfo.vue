<template>
   <el-dialog title="Tips" :visible.sync="bookInfoDialogVisible" width="30%" :before-close="handleClose">
            <span>This is a message</span>
            <span slot="footer" class="dialog-footer">
                <el-button @click="bookInfoDialogVisible = false">Cancel</el-button>
                <el-button type="primary" @click="bookInfoDialogVisible = false">Confirm</el-button>
            </span>
        </el-dialog>
</template>

<script>
    export default {
        name: 'BookInfo',
        props: ['bookInfo', 'bookInfoDialogVisible'],
    }
</script>

<style scoped>

</style>