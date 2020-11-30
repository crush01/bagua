<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		},
		globalData: { // 小程序全局数据
			guaList: require("@/assets/json/gua.json")
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
