<script setup>
    import {faker} from '@faker-js/faker'
    import {ref} from 'vue'
    import useAPI from '@/composables/useAPI'


    const { getDepartment } = useAPI()
    const selectCard = () => {
      console.log(`${props.employee.name} selected`)
    }

    const props = defineProps({
    employee: {
      type: Object,
      required: true,
      default: () => {
        return {
          createdAt: '2022-01-01',
          departmentId: '123',
          email: 'john.doe@example.com',
          employeeId: '123',
          name: 'John Doe',
          quote: 'Really Cool quote',
          title: 'Position',
          updatedAt: '2022-01-01',
        }
      },
    },
  })
  const departmentResponse = await getDepartment(props.employee.departmentId)
  const department = ref(departmentResponse)
</script>

<template>
    <div class ="card" @click="selectCard">
        <div class = "card-image">
            <img :src="faker.internet.avatar()" alt ="" srcset="" />
        </div>
        <div class="card-details">
            <p class="card-details-name">{{ props.employee.name }}</p>
            <p class="card-details-job">{{ props.employee.title }}, {{ department.name }}</p>
            <p class="card-details-quote">"{{ props.employee.quote }}" </p>
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