<template>
    <div style="height: 100vh">
        <iframe scrolling="no" allowtransparency="true" frameborder="0" src="https://s.tradingview.com/embed-widget/hotlists/?locale=en#%7B%22colorTheme%22%3A%22dark%22%2C%22dateRange%22%3A%2212m%22%2C%22exchange%22%3A%22US%22%2C%22showChart%22%3Atrue%2C%22width%22%3A%22100%25%22%2C%22height%22%3A%22100%25%22%2C%22largeChartUrl%22%3A%22%22%2C%22isTransparent%22%3Afalse%2C%22plotLineColorGrowing%22%3A%22rgba(25%2C%20118%2C%20210%2C%201)%22%2C%22plotLineColorFalling%22%3A%22rgba(25%2C%20118%2C%20210%2C%201)%22%2C%22gridLineColor%22%3A%22rgba(42%2C%2046%2C%2057%2C%201)%22%2C%22scaleFontColor%22%3A%22rgba(120%2C%20123%2C%20134%2C%201)%22%2C%22belowLineFillColorGrowing%22%3A%22rgba(33%2C%20150%2C%20243%2C%200.12)%22%2C%22belowLineFillColorFalling%22%3A%22rgba(33%2C%20150%2C%20243%2C%200.12)%22%2C%22symbolActiveColor%22%3A%22rgba(33%2C%20150%2C%20243%2C%200.12)%22%2C%22utm_source%22%3A%22localhost%22%2C%22utm_medium%22%3A%22widget%22%2C%22utm_campaign%22%3A%22hotlists%22%7D" style="box-sizing: border-box; height: 100%; width: 100%;"></iframe>
    </div>
</template>

<script>
export default {
    name: 'StockMarketWidget'
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