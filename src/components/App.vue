<template>
  <Page>
<ActionBar title="App Users" >
<ActionItem ios.position="right">Cristian Torres</ActionItem>
</ActionBar>
    <ListView for="item in dataApi" class="list-group">
      <v-template>
        <GridLayout class="list-group-item" rows="*" columns="auto, *" >
          <Image
            src.decode="font://&#xf007;"
            class="fas ico"
            horizontalAlignment="left"
            style="color:green;"
          />
          <StackLayout class="list-view-item"
            orientation="vertical"
            paddingLeft="50"
            paddingRight="50"
            paddingBotton="0"
            paddingTop= "0"
            style="margin:0;"
          >
            <Label class="h3" :text="item.name"/>
            <Label class="h4" :text="item.email"/>
          </StackLayout>
        </GridLayout>
      </v-template>
    </ListView>
  </Page>
</template>

<script>
export default {
  data() {
    return {
      msg: "Hello World!",
      dataApi: [],
    };
  },
   async mounted() {
    //llamamos metodo para cargar la data
    this.getData();
  },
  methods: {
    //metodo para obtener la data de la api
    async getData() {
      try {
        const response = await fetch(
          "https://jsonplaceholder.typicode.com/users"
        );
        this.dataApi = await response.json();
        console.log(this.dataApi);
      } catch (error) {
        console.log(error);
      }
    },
  },
};
</script>

<style scoped>
ActionBar {
  background-color: #2B8CEE;
  color: #ffffff;
}

.ico {
  color: red;
  font-size: 5;
}
/* label {
  font-size: 20px;
} */

.message {
  vertical-align: center;
  text-align: center;
  font-size: 20;
  color: #333333;
}
</style>
