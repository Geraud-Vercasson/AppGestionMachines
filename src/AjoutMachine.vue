<template>
  <div>
    <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#ajoutModal">
      Ajouter une Machine
    </button>

    <!-- Modal -->
    <div class="modal fade" id="ajoutModal" tabindex="-1" role="dialog" aria-labelledby="ajoutModalCenterTitle"
         aria-hidden="true">
      <div class="modal-dialog modal-dialog-centered" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="ajoutModalLongTitle">Ajouter une machine</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <form v-on:submit="ajout">
            <div class="modal-body">
              <div class="form-group">
                <label for="nomMachineAjout">Nom de la machine</label>
                <input type="text" class="form-control" id="nomMachineAjout" placeholder="Entrez un nom" v-model="machine.name">
              </div>
              <div class="form-group">
                <label for="latitudeMachineAjout">Latitude</label>
                <input type="text" class="form-control" id="latitudeMachineAjout" placeholder="45.1856964" v-model="machine.latitude">
                <label for="longitudeMachineAjout">Longitude</label>
                <input type="text" class="form-control" id="longitudeMachineAjout" placeholder="5.7287321" v-model="machine.longitude">
              </div>
              <div class="form-check">
                <input type="checkbox" class="form-check-input" id="statusMachineAjout" v-model="machine.status">
                <label class="form-check-label" for="statusMachineAjout">Activée</label>
              </div>
            </div>
            <div class="modal-footer">
              <button type="button" class="btn btn-secondary" data-dismiss="modal">Annuler</button>
              <button type="submit" class="btn btn-primary" >Enregistrer</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import axios from 'axios'

  export default {
    name: "ajout-machine",
    data(){
      return {
        machine:{
          name: '',
          status:'false',
          latitude:'45.1856964',
          longitude:'5.7287321',
          checkedAt: 0
        }
      }
    },
    methods:{
      ajout(){
        $('#ajoutModal').modal('hide')
        this.machine.checkedAt = Date().toString()
        if(this.machine.status){
          this.machine.status = 'true'
        } else {
          this.machine.status = 'false'
        }
        axios.post('https://machine-api-campus.herokuapp.com/api/machines',
                    this.machine)
          .then(response =>{
            this.$emit('success')
          })
          .catch(error =>{
            console.log(error)

          })

      }
    }
  }
</script>

<style scoped>

</style>
