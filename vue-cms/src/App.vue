<template>
    <div class="app-container">
        <!-- 顶部Header -->
		<div>
			<mt-header fixed title="Vue项目"></mt-header>
		</div>

        <!-- 中间router-view -->
		<transition mode="out-in">
			<router-view></router-view>
		</transition>

        <!-- 底部Tabber -->
		<div>
			<nav class="mui-bar mui-bar-tab">
				<router-link class="mui-tab-item" to="/home">
					<span class="mui-icon mui-icon-home"></span>
					<span class="mui-tab-label">首页</span>
				</router-link>
				<router-link class="mui-tab-item" to="/member">
					<span class="mui-icon mui-icon-contact"></span>
					<span class="mui-tab-label">会员</span>
				</router-link>
				<router-link class="mui-tab-item" to="/chart">
					<span class="mui-icon mui-icon-extra mui-icon-extra-cart">
						<span class="mui-badge">0</span>
					</span>
					<span class="mui-tab-label">购物车</span>
				</router-link>
				<router-link class="mui-tab-item" to="/search">
					<span class="mui-icon mui-icon-search"></span>
					<span class="mui-tab-label">搜索</span>
				</router-link>
			</nav>
		</div>
    </div>
</template>

<script>

export default {

}
</script>

<style lang="scss" scoped>
.app-container{
	padding-top: 40px;
	padding-bottom: 50px;
	overflow-x: hidden;
}

.v-enter{
	opacity: 0;
	transform: translateX(100%);
}
.v-leave-to{
	opacity: 0;
	transform: translateX(-100%);
}

.v-enter.active,
.v-leave-active{
	transition: 0.2s all ease;
	position:absolute;
}
</style>