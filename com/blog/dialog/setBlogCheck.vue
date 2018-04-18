<template>
    <div class="zm-dialog-check">
        <button class="zm-dialog-check-button" @click.stop="checkBlog()" >选择博客</button>
    </div>
</template>
<script>
export default {
    name:"set-blog-check",
    props:['prop'],
    data(){
        return {}
    },
    methods:{
        checkBlog(){
            let _this =this;
            _this.prop.public.choiceModules({multiple: true, modules: 'blogger',callBack:_this.blogpict});//7-1选择博客数据;
        },
        blogpict(data){
            var fathList = this.prop.lists,
                Data = data.concat(fathList),
                arr = this.prop.public.grouping(Data,"fId"),
                results=[],
                currentData=[];
            for(var i =0;i<arr.length;i++){
                    results.push(arr[i][0]);
            }
            results.forEach((ele)=>{
                ele.isShowBlog = true;
            })
            this.$emit("checkList",results)
        }
    }
}
</script>

