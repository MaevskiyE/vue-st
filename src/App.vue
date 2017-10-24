    <template>
    <div class="base">
        <div class="title">
            The User Components
            <p>I'm awesome user!</p>
            <button @click="changeName">Change Name</button>
        </div>
        <hr>
        <div class="blocks">
            <red :name="name"></red>
            <green :msg="hello"></green>
        </div>
    </div>
</template>

<script>
    import Green from './components/green.vue'
    import Red from './components/red.vue'

    export default {
        data: function() {
            return {
                hello: 'Hello World',
                name: 'Kris'
            };
        },
        components: {
            Green,
            Red
        },
        methods: {
          changeName() {
              this.name = 'Eugen'
          }
        }
    }
</script>

<style scoped>
    .blocks{
        display: flex;
        flex-direction: row;
        justify-content: space-around;
    }
    .base {
        width: 1170px;
        margin: auto;
        display: flex;
        flex-direction: column;
        height: 100%;
        background-color: #ccc;
        padding: 30px;
        box-sizing: border-box;
    }
    .title {
        font-size: 36px;
        font-weight: bold;
        height: 200px;
        border-bottom: 1px solid #fff;
    }

</style>