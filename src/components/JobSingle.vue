<script setup>
    import { computed, defineProps } from 'vue';

    // desta form podes usar o dados job que veio apartir de um componente pai, manejar no componente filho
 const props = defineProps({
        job: Object,
    });

    //const showFullDescription = ref(false);

    // apartir da variavel props podemos usar os dados do object job do componente pai e acessar as suas propriedades no componente filho
   /* const truncatedDescription = computed(() => {
      let description = props.job.description;
      
        if(!showFullDescription.value){

          //a função substring permite limmitar a exibição de texto apartir de um numero pré-determinado
          description = description.substring(0, 90);
        }
        return description;
    }); */
    
</script>

<template>
    <div class="bg-white rounded-xl shadow-md relative">
        <div class="p-4">
          <div class="mb-6">
            <div class="text-gray-600 my-2">{{job.type}}</div>
            <h3 class="text-xl font-bold">{{job.title}}</h3>
          </div>

          <div class="mb-5">
           {{ job.description }}
          </div>

          <h3 class="text-green-500 mb-2"> {{ job.salary }} / Year</h3>

          <div class="border border-gray-100 mb-5"></div>

          <div class="flex flex-col lg:flex-row justify-between mb-4">
            <div class="text-orange-700 mb-3">
              <i class="fa-solid fa-location-dot text-lg"></i>
             {{ job.location }}
            </div>
            <a
              :href="'/jobs/' + job.id"
              class="h-[36px] bg-green-500 hover:bg-green-600 text-white px-4 py-2 rounded-lg text-center text-sm"
            >
              Read More
            </a>
          </div>
        </div>
      </div>
</template>