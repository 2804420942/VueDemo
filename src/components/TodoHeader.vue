<template>
	<div class="todo-header">
		<input type="text" placeholder="请输入你的任务名称，按回车键确认" @keyup.enter='addItem' 
		v-model="title"/>
	</div>
</template>
<script type="text/javascript">
	export default{
		data(){
			return {
				title: ''
			}
		},
		methods: {
			addItem(){
				//1,检查输入的合法性
				const title = this.title.trim();
				if(!title){
					alert("输入不能为空");
					return
				}
				//2,根据输入输出一个todo对象
				const todo = {
					title,
					complete:false
				};
				//3,添加到todos
				//this.addTodo(todo);
				this.$store.dispatch('addTodo',todo);
				//4,清除输入
				this.title = '';
			}
		}
	}
</script>
<style type="text/css">
	/*header*/
	.todo-header input {
	  width: 560px;
	  height: 28px;
	  font-size: 14px;
	  border: 1px solid #ccc;
	  border-radius: 4px;
	  padding: 4px 7px;
	}

	.todo-header input:focus {
	  outline: none;
	  border-color: rgba(82, 168, 236, 0.8);
	  box-shadow: inset 0 1px 1px rgba(0, 0, 0, 0.075), 0 0 8px rgba(82, 168, 236, 0.6);
	}
</style>