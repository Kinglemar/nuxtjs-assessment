 <template>
      <div>
        <div class="navbar">
          <Navbar :link="prev"/>
          <Navbar :link="next"/>
        </div>

        <div id="page1">
          <div class="header">Debounced search:</div>
          <div class="content">
            <div class="flex-row">
              <label class="label" for="search">Search:</label>
              <input v-model="searchQuery" @keydown="controlDataRefresh" @keyup="getApiData" class="input" type="text">
            </div>

            <p v-if="isSearching">Searching…</p>

            <div v-else class="list">
              <span v-for="result in results" :key="result" class="list-item">{{ result }}</span>
            </div>
          </div>
        </div>
        </div>
</template>

    <script>
    import _ from 'lodash';
    import Navbar from '../components/Navbar.vue';

    const kDataset = ["Java", "JavaScript", "Python", "Vue.js", "React", "Angular"];
    // const kDataset = []
    const kDebounceTimeoutMs = 1000;

    export default {
    name: "IndexPage",

    data(){
        return{
          searchQuery : "",
          isSearching : false,
          searchDatabase: "",
          prev: {
            name: 'Previous',
            path: '/'
          },
          next: {
            name: 'Next',
            path: '/Page2'
          }
        }
    },
//temporarily stop API request

    methods: {
    getApiData: _.debounce( function(){
      this.isSearching = !this.isSearching
      console.log('Api Data requested!')

      // const res = await fetch('https://busy.io')
      // const data = await res.json

      // set response to kDataset
      // kDataset = data
    }, kDebounceTimeoutMs),

      controlDataRefresh : _.debounce( function(){
        if(this.results){
          this.isSearching = !this.isSearching
          console.log("warned")
        }
    }, 10)
    },

    computed: {
        results() {
        return this.searchQuery
            ? kDataset.filter(string =>
                string.toLowerCase().includes(this.searchQuery.toLowerCase())
            )
            : kDataset;
        },
    },

    components: {
        Navbar
    },
    }
    </script>

<style scoped>
#page1 {
  font-family: "Roboto", helvetica, arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  padding: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  position: relative;

  background: linear-gradient(
    135deg,
    rgba(65, 184, 131, 0.9),
    rgba(52, 73, 94, 0.9)
  );

  font-size: 1.5em;
}

.navbar{
  display: flex;
  justify-content: space-evenly;
}
.content {
  width: 100%;
  padding: 2em;
  margin-top: 30px;
  position: relative;
  background: rgba(0, 0, 0, 0.15);
}

@media screen and (min-width: 600px) {
  .content {
    width: 50vw;
    max-width: 15em;
  }
}

.content::before {
  content: "";
  position: absolute;
  top: -2px;
  left: 0;
  height: 2px;
  width: 100%;

  background: #35c3c1;
}

.flex-row {
  display: flex;
  margin-bottom: 1em;
}

.label {
  width: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 12px;

  background: #f5f6f8;
}

.input {
  flex: 1;
  padding: 1em;
  border: 0;
  color: #8f8f8f;
  font-size: 1rem;
}

.list {
  padding: 0;
}

.list-item {
  transition: all 300ms;
  display: block;
  margin-top: 10px;
}
</style>