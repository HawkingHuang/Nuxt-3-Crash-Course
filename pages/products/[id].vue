<script setup>
  const { id } = useRoute().params

  const { data: product } = await useFetch(`https://fakestoreapi.com/products/${id}`)

  if(!product.value) {
    throw createError({
      statusCode: 404,
      statusMessage: 'Product not found',
      fatal: true
    })
  }

  definePageMeta({
    layout: 'products'
  })
</script>

<template>
  <div>
    <ProductDetails :product="product" />
  </div>
</template>
