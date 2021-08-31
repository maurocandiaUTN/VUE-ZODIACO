<template>
 
<div style="margin-top:80px">
    

    <b-card-group deck>
      <div v-for="zodi in enero" :key="zodi.id" style="margin-top: 10px">
        <zodiacos :propiedadZodiaco="zodi"></zodiacos>
      </div>
    </b-card-group>
  </div>
 
</template>




<script>
import zodiacos from "@/components/zodiacos";
import MenuSuperiorDeOpciones from "@/components/MenuSuperiorDeOpciones";
export default {
  name: "AgrupaMes",
  components: {
    zodiacos,
    MenuSuperiorDeOpciones
  },
 
  mounted() {
    this.MesEnero()
  },
  data() {
    return {
      zodiacoEncontrado: [],
      enero:[],
    
    };
  },
  
  methods: {
    async MesEnero() {
      
      const parametroId = this.$route.params.id;
        await fetch("http:/test/tb/zodiaco.json")
          .then((res) => res.json()) 
          
          .then((data) => (this.zodiacoEncontrado = data));
          
        this.zodiacoEncontrado.map((signo, i) => {
          if (signo.meses[0] == parametroId || signo.meses[1] == parametroId) {
            this.enero.push(signo);
            
            
          }

        }
        )
        console.log(this.enero)
      },
  },
};
</script>
