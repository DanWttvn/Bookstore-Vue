<template>

	<div class="header">
		<h1>UBIQUM BOOKSTORE</h1>
		<div class="mascara"></div>
		<img src="../assets/books-img.jpg" alt="libros">
	</div>

</template>




<script>
export default {
	name: "Header",
}
</script>



<style>

	.header {
		position: relative;
		width: 100%;
		height: 250px;
		overflow: hidden;
		display: flex;
		flex-flow: row wrap;
		justify-content: center;
		align-items: center;

		color: #fff;
	}

	h1 {
		position: absolute;
		z-index: 10;
		margin: auto;

		text-align: center;
		font-family: 'Montserrat', sans-serif;
		font-weight: 700;
		font-size: 50px;
	}

	.header img {
		position: absolute;
		z-index: 1;
	}

	.mascara {
		z-index: 5;
		width: 100%;
		height: 100%;
		background: #000;
		opacity: 0.2;
	}

</style>
