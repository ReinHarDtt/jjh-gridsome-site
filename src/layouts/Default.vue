<template>
	<div class="layout">
		<header class="header sticky">
			<div class="container">
				<div class="left">
					<g-link to="/">
						<img
							class="logo"
							src="data:image/svg+xml;base64,PD94bWwgdmVyc2lvbj0iMS4wIiBlbmNvZGluZz0idXRmLTgiPz4KPCEtLSBHZW5lcmF0b3I6IEFkb2JlIElsbHVzdHJhdG9yIDE5LjIuMSwgU1ZHIEV4cG9ydCBQbHVnLUluIC4gU1ZHIFZlcnNpb246IDYuMDAgQnVpbGQgMCkgIC0tPgo8c3ZnIHZlcnNpb249IjEuMSIgaWQ9IkxheWVyXzEiIHhtbG5zPSJodHRwOi8vd3d3LnczLm9yZy8yMDAwL3N2ZyIgeG1sbnM6eGxpbms9Imh0dHA6Ly93d3cudzMub3JnLzE5OTkveGxpbmsiIHg9IjBweCIgeT0iMHB4IgoJIHZpZXdCb3g9IjAgMCA1Mi4zIDIwLjkiIHN0eWxlPSJlbmFibGUtYmFja2dyb3VuZDpuZXcgMCAwIDUyLjMgMjAuOTsiIHhtbDpzcGFjZT0icHJlc2VydmUiPgo8Zz4KCTxwYXRoIGQ9Ik0xMC41LDAuMWMtMC42LTAuMy0xLjQsMC0xLjYsMC42TDAuMSwxOS4xYy0wLjMsMC42LTAuMSwxLjMsMC41LDEuNmMwLjIsMC4xLDAuNCwwLjEsMC41LDAuMWMwLjQsMCwwLjktMC4yLDEuMS0wLjcKCQlMMTEsMS43QzExLjMsMS4xLDExLjEsMC40LDEwLjUsMC4xeiIvPgoJPHBhdGggZD0iTTQxLjMsNC4yYy0wLjYtMC4zLTEuMywwLTEuNiwwLjZsLTYuMywxMy4zYy0wLjEsMC4yLTAuMiwwLjMtMC4zLDAuNGMtMC4xLDAtMC4yLTAuMS0wLjMtMC4zbC0xLjktNAoJCWMtMC42LTEtMS40LTEuNS0yLjQtMS41Yy0wLjksMC0xLjgsMC43LTIuMywxLjdsLTEuNywzLjdjLTAuMSwwLjEtMC4xLDAuMi0wLjIsMC4zYzAtMC4xLTAuMS0wLjItMC4xLTAuM2wtMy02LjIKCQljLTAuMy0wLjYtMS0wLjgtMS42LTAuNXMtMC44LDEtMC41LDEuNmwzLDYuM2MwLjUsMS4xLDEuNCwxLjYsMi4zLDEuNmwwLDBjMC45LDAsMS44LTAuNSwyLjMtMS42bDEuNy0zLjhjMC4xLTAuMywwLjMtMC40LDAuMy0wLjQKCQlzMC4xLDAuMSwwLjMsMC40bDEuOSw0YzAuNiwwLjksMS40LDEuNSwyLjMsMS41aDAuMWMwLjktMC4xLDEuOC0wLjcsMi4zLTEuN0w0MS45LDZDNDIuMSw1LjIsNDEuOSw0LjUsNDEuMyw0LjJ6Ii8+Cgk8cGF0aCBkPSJNNTIuMSwxOS4xTDQzLjQsMC43Yy0wLjMtMC42LTEtMC44LTEuNi0wLjVzLTAuOCwxLTAuNSwxLjZMNTAsMjAuMmMwLjIsMC40LDAuNiwwLjcsMS4xLDAuN2MwLjIsMCwwLjQsMCwwLjUtMC4xCgkJQzUyLjIsMjAuNCw1Mi40LDE5LjcsNTIuMSwxOS4xeiIvPgoJPHBhdGggZD0iTTIyLjYsMi41YzAuMSwwLjEsMC4xLDAuMSwwLjIsMC4zbDQuMSw4LjZjMC4zLDAuNiwxLjEsMC43LDEuNywwLjRzMC43LTEuMSwwLjQtMS43bC00LjEtOC42Yy0wLjYtMS0xLjUtMS41LTIuNC0xLjUKCQljLTAuOSwwLjEtMS43LDAuNy0yLjIsMS44bC03LjcsMTYuM2MtMC4xLDAuMS0wLjEsMC4yLTAuMSwwLjNjMC0wLjEtMC4xLTAuMS0wLjItMC4zbC0zLTYuMmMtMC4zLTAuNi0xLjEtMC44LTEuNi0wLjUKCQlDNywxMS43LDYuOCwxMi41LDcuMSwxM2wzLDYuMmMwLjYsMSwxLjQsMS42LDIuMywxLjZoMC4xYzAuOSwwLDEuNy0wLjcsMi4yLTEuOGw3LjctMTYuM0MyMi41LDIuNiwyMi41LDIuNSwyMi42LDIuNXoiLz4KCTxwYXRoIGQ9Ik00NiwxNC4yYy0wLjYtMC4zLTEuMy0wLjEtMS42LDAuNWwtMS42LDMuNGMtMC4xLDAuMi0wLjIsMC4zLTAuMiwwLjNjLTAuMSwwLTAuMS0wLjEtMC4yLTAuM2wtMS42LTMuNAoJCWMtMC4zLTAuNi0xLTAuOC0xLjYtMC41cy0wLjgsMS0wLjUsMS42bDEuNiwzLjRjMC42LDEsMS40LDEuNiwyLjMsMS42YzAuOSwwLDEuOC0wLjYsMi4zLTEuNmwxLjYtMy40QzQ2LjgsMTUuMiw0Ni42LDE0LjUsNDYsMTQuMgoJCXoiLz4KPC9nPgo8L3N2Zz4K"
							alt=""
						/>
					</g-link>
				</div>
				<div class="nav right">
					<g-link class="nav__link" to="/404">Journal</g-link>
					<g-link class="nav__link" to="/404">Say Hi!</g-link>
				</div>
			</div>
		</header>
		<slot />
		<div>
			<div class="latest-journals-heading container">
				<span class="label">Latest and greatest</span>
			</div>
			<div class="latest-journals">
				<div class="container">
					<a href="/journal/gridsome-forestry-cms/" class="journal"
						><h3 class="journal-title">Gridsome with Forestry CMS</h3></a
					><a href="/journal/use-gridsome-vuejs/" class="journal"
						><h3 class="journal-title">VueJS for your next project</h3></a
					><a href="/journal/macos-development-environment/" class="journal"
						><h3 class="journal-title">macOS development environment</h3></a
					><a href="/journal/a-journal-entry/" class="journal"><h3 class="journal-title">About Typography</h3></a>
				</div>
			</div>
		</div>
		<footer data-v-07acb5f8="" class="footer">
			<div data-v-07acb5f8="" class="container"><span data-v-07acb5f8="">Copyright © 2021</span></div>
		</footer>
	</div>
</template>

<style lang="less">
* {
	box-sizing: border-box;
	color: #000;
}
img {
	max-width: 100%;
}
body {
	font-family: -apple-system, system-ui, BlinkMacSystemFont, 'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
	margin: 0;
	padding: 0;
	line-height: 1.5;
}

.layout {
	padding: 6rem 0 0;
	/* max-width: 760px;
	margin: 0 auto;
	padding-left: 20px;
	padding-right: 20px; */
}
.container {
    max-width: 1200px;
    margin: 0 auto;
    padding: 0 2rem;
}
.header {
	position: fixed;
	top: 0;
	left: 0;
	width: 100%;
	height: 6rem;
	z-index: 10;
	.container {
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 100%;
		.logo {
			height: 1.5rem;
		}
		.nav__link {
			font-size: 0.9rem;
			font-weight: 600;
			text-decoration: none;
			margin-top: 4px;
			margin-right: 3rem;
			padding-bottom: 4px;
			border-bottom: 1px solid;
			border-color: transparent;
			transition: border 0.15s;
		}
	}
}
.latest-journals-heading {
	margin-top: 6rem;
	margin-bottom: 1rem;
	font-size: 0.6rem;
	font-weight: 400;
	text-transform: uppercase;
	.label {
		display: block;
		font-weight: 700;
		margin-bottom: 0.5rem;
	}
}
.latest-journals {
	max-width: 100%;
	margin: 0 2rem;
  border: 1px solid #f3f3f3;
  .container {
    display: flex;
    flex-wrap: wrap;
  }
}
.journal {
	flex: 0 0 100%;
	display: block;
	padding: 2rem;
	transition: all 0.25s ease;
	text-decoration: none;
	border-bottom: 1px solid #f3f3f3;
}
.journal-title {
    font-size: 1rem;
    line-height: 1.35;
}
.footer {
	font-size: 0.8rem;
	padding: 6rem 0;
}
@media (min-width: 920px) {
	.latest-journals {
		margin: 0;
		border-left: 0;
		border-right: 0;
		border-top: 1px solid #f3f3f3;
		border-bottom: 1px solid #f3f3f3;
	}
}
@media (min-width: 920px) {
	.journal:first-child,
	.journal:nth-child(2),
	.journal:nth-child(3) {
		border: 0;
		border-right: 1px solid #f3f3f3;
	}
}

@media (min-width: 920px) {
	.journal {
		flex: 0 0 25%!important;
	}
}

@media (min-width: 580px) {
	.journal:first-child,
	.journal:nth-child(2) {
		border-bottom: 1px solid #f3f3f3;
	}
}
@media (min-width: 580px) {
	.journal:first-child {
		border-right: 1px solid #f3f3f3;
	}
}
@media (min-width: 580px) {
	.journal {
		flex: 0 0 50%;
	}
}

@media (min-width: 860px) {
	.container {
		padding: 0 6rem;
	}
}
</style>
