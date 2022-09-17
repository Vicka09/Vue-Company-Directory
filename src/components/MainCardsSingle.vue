<script setup>
    import {faker} from '@faker-js/faker'
    const firstName = faker.name.firstName();
    const lastName = faker.name.lastName();
    const fullName = `${firstName} ${lastName}`

    const selectCard = () => {
      console.log(`${fullName} selected`)
    }
</script>

<template>
    <div class ="card" @click="selectCard">
        <div class = "card-image">
            <img :src="faker.internet.avatar()" alt ="" srcset="" />
        </div>
        <div class="card-details">
            <p class ="card-details-name">{{ fullName }}</p>
            <p class ="card-details-job">{{ faker.name.jobTitle() }}, {{faker.name.jobArea()}}</p>
            <p class ="card-details=email">{{ faker.internet.exampleEmail(firstName,lastName) }}</p>
            <p class ="card-details-quote">{{ faker.lorem.paragraph() }}</p>
        </div>
    </div>
</template>

<style scoped lang="postcss">

    .card {
        @apply cursor-pointer overflow-hidden rounded-2xl bg-stone-100 p-8 shadow-lg transition-transform duration-300 hover:scale-110 hover:shadow-slate-900 hover:shadow-2xl;
    &-image{
        img{
            @apply mx-auto rounded-full object-contain;
        }
    }

    &-details {
        @apply flex flex-col gap-3 pt-6 text-center;
        &-name {
            @apply text-3xl font-semibold tracking-wide text-amber-800;
        }
        &-job {
            @apply -mt-2 text-xs text-amber-600;
        }
        &-email{
            @apply text-sm text-stone-600;
        }
        &-quote{
            @apply italic text-lg text-stone-600;
        }
    }
   
    }



</style>