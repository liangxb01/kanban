<script>
	export default {
		onLaunch: function() {
			console.log('App Launch')
			// #ifdef APP-PLUS
					    plus.navigator.setFullscreen(true);//隐藏手机顶部状态栏
					    plus.navigator.hideSystemNavigation();//隐藏手机底部导航按键
					    // #endif
						// #ifdef APP-PLUS
						plus.screen.lockOrientation('landscape-primary'); //锁定横屏
						plus.navigator.setFullscreen(true); //隐藏状态栏(应用全屏:只能隐藏状态栏，标题栏和虚拟返回键都还可以显示)		
						// #endif
		},
		onShow: function() {
			console.log('App Show')
		},
		onHide: function() {
			console.log('App Hide')
		}
	}
</script>

<style>
	/*每个页面公共css */
</style>
