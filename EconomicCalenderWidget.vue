<template>
  <div class="h-screen">
    <div class="tradingview-widget-container" style="width: 100%; height: 100%;">
        <iframe scrolling="no" allowtransparency="true" frameborder="0" src="https://s.tradingview.com/embed-widget/events/?locale=en#%7B%22colorTheme%22%3A%22dark%22%2C%22isTransparent%22%3Afalse%2C%22width%22%3A%22100%25%22%2C%22height%22%3A%22100%25%22%2C%22importanceFilter%22%3A%220%2C1%22%2C%22utm_source%22%3A%22localhost%22%2C%22utm_medium%22%3A%22widget_new%22%2C%22utm_campaign%22%3A%22events%22%7D" style="box-sizing: border-box; height: calc(100% - 32px); width: 100%;"></iframe>    
    </div>
  </div>
</template>

<script>
export default {
    name: 'EconomicCalenderWidget'
}
</script>

<style scoped>
    .tradingview-widget-copyright {
		font-size: 13px !important;
		line-height: 32px !important;
		text-align: center !important;
		vertical-align: middle !important;
		font-family: 'Trebuchet MS', Arial, sans-serif !important;
		color: #9db2bd !important;
	}

	.tradingview-widget-copyright .blue-text {
		color: #2196f3 !important;
	}

	.tradingview-widget-copyright a {
		text-decoration: none !important;
		color: #9db2bd !important;
	}

	.tradingview-widget-copyright a:visited {
		color: #9db2bd !important;
	}

	.tradingview-widget-copyright a:hover .blue-text {
		color: #38acdb !important;
	}

	.tradingview-widget-copyright a:active .blue-text {
		color: #299dcd !important;
	}

	.tradingview-widget-copyright a:visited .blue-text {
		color: #2196f3 !important;
	}
</style>