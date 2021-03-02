<template>
	<Layout>
		<div class="container">
			<div class="hero">
				<h1 class="hero-title">{{ $page.homeInfo.title }}</h1>
				<h2 class="hero-subtitle">
					{{ $page.homeInfo.desc }}
				</h2>
			</div>
			<div class="projects">
				<div class="project" v-for="project in $page.homeInfo.projects" :key="project.title">
					<g-image
						class="thumbnail"
						:src="`${GRIDSOME_API_URL + project.thumbnail.url}`"
					/>
					<h3 class="project-title">{{ project.title }}</h3>
					<div class="categories"><span class="category" v-for="category in project.categories.split(',')" :key="category">{{ category }}</span></div>
				</div>
			</div>
		</div>
	</Layout>
</template>

<page-query>
query {
  homeInfo: strapiBlogHomeInfo (id: 1) {
    id
    title
    desc
    projects {
      title
      categories
      thumbnail {
        url
      }
    }
  }
}
</page-query>

<script>
export default {
	metaInfo: {
		title: 'Hello, world!',
  },
  mounted() {
    console.log(this.$page.homeInfo);
  }
}
</script>

<style lang="less" scoped>
.container {
	max-width: 1200px;
	margin: 0 auto;
	padding: 0 2rem;
	.hero {
		text-align: center;
		width: 480px;
		max-width: 100%;
		margin: 0 auto;
		padding: 4rem 0 8rem;
	}
	.hero-title {
		font-size: 3rem;
		font-weight: 700;
		padding: 0;
		margin: 0 0 2rem;
	}
	h1 {
		letter-spacing: -0.01em;
	}
	.hero-subtitle {
		font-size: 1.15em;
		font-weight: 400;
		line-height: 1.68;
		opacity: 0.6;
		margin: 0;
		padding: 0;
	}
	.projects {
		display: grid;
		grid-template-columns: 1fr 1fr;
		grid-gap: 4rem;
		.project {
			grid-column: auto/span 2;
			text-align: center;
			.thumbnail {
				height: 560px;
				object-fit: cover;
				transition: all 0.15s ease;
				box-shadow: 0 0 40px -20px rgb(0 0 0 / 25%);
			}
			.project-title {
				font-size: 1rem;
				margin: 2rem 0 1rem;
			}

			.categories {
				font-size: 0.8rem;
				color: #2b2b2b;
				.category {
					margin-right: 0.8rem;
				}
			}
		}
		@media (min-width: 920px) {
			.project {
				grid-column: auto/span 1;
			}
		}
		@media (min-width: 920px) {
			.project:nth-child(3n + 1) {
				grid-column: auto/span 2;
			}
		}
	}
}
@media (min-width: 860px) {
	.container {
		padding: 0 6rem;
	}
}
</style>
