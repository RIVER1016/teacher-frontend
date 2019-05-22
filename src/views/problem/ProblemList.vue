<template>
	<div class="ant-layout-has-sider" >
		<div class="title">
			<h1 class="title-text">添加题目</h1>
			<div class="view">
				<a href="./ProblemDetail.vue" disabled="">编辑</a>
				<div class="ant-divider ant-divider-vertical"></div>
				<a href="">预览</a>
			</div>
		</div>
		<div class="ant-divider ant-divider-horizontal"></div>
		<div class="main">
			<div class="problem-title">
				<a-icon class="title-icon" type="caret-right" /><h3>题目标题</h3>
				<input type="text" class="ant-input">
			</div>
			<div class="problem-block">
				<a-icon class="title-icon" type="caret-right" /><h3>题目类型</h3>
				<div class="ant-radio-group ant-radio-group-outline ant-radio-group-default" style="margin-bottom: 16px;">
					<label class="ant-radio-button-wrapper radio-button-wrapper">
						<span class="ant-radio-button radio-button">
							<input type="radio" class="ant-radio-button-input" value="practice">
						</span>
						<span id="practice_type">练习题</span>
					</label>
					<label class="ant-radio-button-wrapper radio-button-wrapper">
						<span class="ant-radio-button radio-button">
							<input type="radio" class="ant-radio-button-input" value="exam">
						</span>
						<span id="exam_type">考试题</span>
					</label>
					<label class="ant-radio-button-wrapper radio-button-wrapper">
						<span class="ant-radio-button radio-button">
							<input type="radio" class="ant-radio-button-input" value="homework">
						</span>
						<span id="homework_type">作业题</span>
					</label>
				</div>
			</div>
			<div class="problem-block" id="multi-textarea">
				<a-icon class="title-icon" type="caret-right" /><h3>题目描述</h3>
               <editor></editor>
			</div>
			<div class="problem-block">
				<a-icon class="title-icon" type="caret-right" /><h3>附件</h3>
				<button type="button" class="ant-btn ant-btn-default">
					<i class="anticon anticon-upload">
						<svg viewBox="64 64 896 896" data-icon="upload" width="1em" height="1em" fill="currentColor" aria-hidden="true" class="">
							<path d="M400 317.7h73.9V656c0 4.4 3.6 8 8 8h60c4.4 0 8-3.6 8-8V317.7H624c6.7 0 10.4-7.7 6.3-12.9L518.3 163a8 8 0 0 0-12.6 0l-112 141.7c-4.1 5.3-.4 13 6.3 13zM878 626h-60c-4.4 0-8 3.6-8 8v154H214V634c0-4.4-3.6-8-8-8h-60c-4.4 0-8 3.6-8 8v198c0 17.7 14.3 32 32 32h684c17.7 0 32-14.3 32-32V634c0-4.4-3.6-8-8-8z">
							</path>
						</svg>
					</i>
					<span>上传附件</span></button>
			</div>
			<div class="problem-block" id="limit">
				<div class="problem-limit">
					<a-icon class="title-icon" type="caret-right" /><h3>内存限制(MB)</h3>
					<input type="text" class="ant-input limit-input" name="memory_limit">
				</div>
				<div class="problem-limit">
					<a-icon class="title-icon" type="caret-right" /><h3>时间限制(MS)</h3>
					<input type="text" class="ant-input limit-input" name="time_limit">
				</div>
				<div class="problem-limit">
					<a-icon class="title-icon" type="caret-right" /><h3>输入限制(行)</h3>
					<input type="text" class="ant-input limit-input" name="input_limit">
				</div>
				<div class="problem-limit">
					<a-icon class="title-icon" type="caret-right" /><h3>输出限制(行)</h3>
					<input type="text" class="ant-input limit-input" name="output_limit">
				</div>
			</div>
			<div class="problem-block">
				<a-icon class="title-icon" type="caret-right" /><h3>测例输入与输出</h3>
				<div class="test-span">
					<div class="test-span-text">
						<a-icon class="title-icon test-input-span" type="caret-right" /><h3>测例标签</h3>
					</div>
					<input type="text" class="ant-input span-input" name="test_span" placeholder="例：边界条件" >
				</div>
				<!--
                	作者：754159742@qq.com
                	时间：2019-05-21
                	描述：需要代码输入框插件
                -->
		             <button type="button" class="ant-btn ant-btn-primary" >
		             	<span>添加>></span>
		             </button>
			</div>
			<div class="problem-block">
				<a-icon class="title-icon" type="caret-right" /><h3>样例输入与输出</h3>
				<div class="test-span">
					<div class="test-span-text">
						<a-icon class="title-icon test-input-span" type="caret-right" /><h3>样例标签</h3>
					</div>
					<input type="text" class="ant-input span-input" name="test_span" placeholder="例：边界条件" >
				</div>
                <div class="test-input-output">
		             <button type="button" class="ant-btn ant-btn-primary" >
		             	<span>添加>></span>
		             </button>
		             <button type="button" class="ant-btn ant-btn-default" >
		             	<span>预览</span>
		             </button>
	             </div>
			</div>
			<div class="problem-block">
				<a-icon class="title-icon" type="caret-right" /><h3>题目标签</h3>
				<div role="combobox" aria-autocomplete="list" aria-haspopup="true" aria-controls="6bd2c6f4-5646-4511-d3de-c4868f4f3148" class="ant-select-selection ant-select-selection--multiple">
					<div class="ant-select-selection__rendered">
						<div unselectable="on" class="ant-select-selection__placeholder" style="display: none; user-select: none;">
							Please select</div>
							<ul>
								<li unselectable="on" role="presentation" title="a1" class="ant-select-selection__choice" style="user-select: none;">
									<div class="ant-select-selection__choice__content">a1</div>
									<span class="ant-select-selection__choice__remove">
										<i class="ant-select-remove-icon anticon anticon-close">
											<svg viewBox="64 64 896 896" data-icon="close" width="1em" height="1em" fill="currentColor" aria-hidden="true" class="">
												<path d="M563.8 512l262.5-312.9c4.4-5.2.7-13.1-6.1-13.1h-79.8c-4.7 0-9.2 2.1-12.3 5.7L511.6 449.8 295.1 191.7c-3-3.6-7.5-5.7-12.3-5.7H203c-6.8 0-10.5 7.9-6.1 13.1L459.4 512 196.9 824.9A7.95 7.95 0 0 0 203 838h79.8c4.7 0 9.2-2.1 12.3-5.7l216.5-258.1 216.5 258.1c3 3.6 7.5 5.7 12.3 5.7h79.8c6.8 0 10.5-7.9 6.1-13.1L563.8 512z">
												</path>
											</svg>
										</i>
									</span>
								</li>
								<li class="ant-select-search ant-select-search--inline">
									<div class="ant-select-search__field__wrap">
										<input autocomplete="off" value="" class="ant-select-search__field" style="">
										<span class="ant-select-search__field__mirror">&nbsp;</span>
									</div>
								</li>
							</ul>
					</div>
				</div>
			</div>	
			<div class="problem-block">
				<a-icon class="title-icon" type="caret-right" /><h3>状态</h3>
				<div class="ant-radio-group ant-radio-group-outline ant-radio-group-default" style="margin-bottom: 16px;">
					<label class="ant-radio-button-wrapper ">
						<span class="ant-radio-button">
							<input type="radio" class="ant-radio-button-input" value="high">
						</span>
						<span id="public">公开</span>
					</label>
					<label class="ant-radio-button-wrapper">
						<span class="ant-radio-button">
							<input type="radio" class="ant-radio-button-input" value="medium">
						</span>
						<span id="private">不公开</span>
					</label>
				</div>
				<div class="ant-radio-group ant-radio-group-outline ant-radio-group-default second-radio-group" style="margin-bottom: 16px;">
					<label class="ant-radio-button-wrapper radio-button-wrapper">
						<span class="ant-radio-button radio-button">
							<input type="radio" class="ant-radio-button-input" value="high">
						</span>
						<span id="high">High</span>
					</label>
					<label class="ant-radio-button-wrapper radio-button-wrapper">
						<span class="ant-radio-button radio-button">
							<input type="radio" class="ant-radio-button-input" value="medium">
						</span>
						<span id="medium">Medium</span>
					</label>
					<label class="ant-radio-button-wrapper radio-button-wrapper">
						<span class="ant-radio-button radio-button">
							<input type="radio" class="ant-radio-button-input" value="low">
						</span>
						<span id="low">Low</span>
					</label>
				</div>
			</div>	
			<div class="btn-block">
				<button type="button" class="ant-btn ant-btn-primary" >
	             	<span>保存</span>
	             </button>
				<button type="button" class="ant-btn ant-btn-default" id="preread">
	             	<span>预览</span>
	             </button>
            </div>
		</div>
	</div>
</template>

<script>
import Editor from './Editor'
	
export default {
	name: 'multi-textarea',
	components:{
		Editor
	}
}
</script>
    
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.title{
	width: 100%;
	height: 3%;
}
.title-text{
	font-size: 20px;
	float: left;
}
.view{
	float: right;
}
.main{
	margin-left: 3%;
}
.problem-title{
	margin-top: 3%;
}
.title-icon{
	float: left;
	font-size: 20px;
}
.ant-input{
	width: 80%;
}
.problem-block{
	margin-top: 2%;
	display: block;
}
.radio-button{
	height: 10px;
}
.radio-button-wrapper{
	height: 50px;
}
#practice_type,#high{
	color: red;
}
#exam_type,#medium{
	color: yellow;
}
#homework_type,#low{
	color: deepskyblue;
}

.limit-input{
	width: 90%;
}
.test-span{
	margin-left: 3%;
	margin-top: 2%;
	display: flex;
}
.test-span-text{
	width: 10%;
	height: 2%;
}
.span-input{
	width: 15%;
}
.second-radio-group{
	margin-left: 5%;
}
#preread{
	margin-left: 1%;
}
.btn-block{
	margin-top: 3%;
}
.ant-select-selection{
	width: 20%;
	height: 100px;
}
#limit{
	display: flex;
}
</style>
