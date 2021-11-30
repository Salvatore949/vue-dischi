<template>
    <div>
        <form action="">
                Scegli il genere
            <select name="genre" v-model="selected" @change=" selezionato ">
                <option value="Rock">Rock</option>
                <option value="Pop">Pop</option>
                <option value="Jazz">Jazz</option>
                <option value="Metal">Metal</option>
            </select>  
        </form>
    </div>    
</template>

<script>
export default {
 name: 'Search',
 data() {
    return {
        selected: null,
    }
 },
 methods: {
     selezionato(){
         this.$emit("selezionato", this.selected)
     },
 }
}
</script>

<style>

</style>