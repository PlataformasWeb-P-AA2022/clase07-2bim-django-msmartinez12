<template>
    <div class="tasks_container">
        <div class="tasks_content">
            <h1>Listado de Numeros</h1>
            <!--ul class="tasks_list"-->
                <span v-for="numerost in tasks" :key="numerost.telefono">
                    <p><b>Telefono:</b> {{ numerost.telefono }}</p>
                    <p><b>Tipo:</b> {{ numerost.tipo }}</p>

                    <hr>
                </span>
            <!--/ul-->
        </div>
    </div>
  <hr>
</template>

<script>
    export default {
        data() {
            return {
                // tasks
                tasks: [''],
                telefono: '',
                tipo: '',
            }
        },
        methods: {
            async getData() {
                try {
                    // fetch tasks
                    const response = await this.$http.get('http://localhost:8000/api/numerost/');
                    // set the data returned as tasks
                    this.tasks = response.data;
                } catch (error) {
                    // log the error
                    console.log("aa" + error);
                }
            },
        },
        created() {
            // Fetch tasks on page load
            this.getData();
        }
    }
</script>