<template>
  <div class="content-area">
    <form class="form-todo" v-on:submit="handleForm">
      <input type="text" autocomplete="off" name="newtodo" :class="{validate:validate}" placeholder="What you want to do?" v-model="newData.title" v-on:input="handleInput()">
      <button type="submit" name="button">+</button>
    </form>
    <ul class="item-lists">
      <p v-if="datas.length===0">Nai Kicchu</p>
      <li v-for="data in datas">
        <span :class={done:data.done} v-on:click="handleDone(data)">{{data.title}}<button v-on:click="handleRemove(data)">X</button></span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'ContentArea',
  data () {
    return {
      newData: {},
      datas: [
        {
          title: 'delectus aut autem',
          done: false
        }, {
          title: 'quis ut nam facilis et officia qui',
          done: true
        }, {
          title: 'fugiat veniam minus',
          done: false
        }, {
          title: 'et porro tempora',
          done: true
        }, {
          title: 'laboriosam mollitia et enim quasi adipisci quia ',
          done: false
        }, {
          title: 'qui ullam ratione quibusdam voluptatem quia omnis',
          done: true
        }
      ],
      validate: false,
      touched: false
    }
  },
  methods: {
    handleForm: function(e) {
      e.preventDefault();
      if(!this.newData.title) {
        this.validate = true;
      } else {
        this.datas = [{title: this.newData.title, done: false}, ...this.datas];
        this.newData = {};
        this.validate = false;
      }
    },
    handleRemove: function(data) {
      this.datas = this.datas.filter(onedata => onedata !== data);
    },
    handleDone: function(data) {
      this.datas.map((onedata,index) => onedata === data ? (onedata.done === false ? onedata.done=true : onedata.done=false) : null);
    },
    handleInput: function() {
      this.validate = false;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .content-area {
    width: 570px;
    background: #fff;
    margin: 0 auto;
    border-radius: 4px;
    padding: 30px;
    -webkit-box-shadow: 0 0 18px -5px rgba(0,0,0,.25);
    box-shadow: 0 0 18px -5px rgba(0,0,0,.25);
  }

  form {
    position: relative;
  }

  input {
    padding: 15px;
    border: 2px solid transparent;
    width: 100%;
    border-radius: 4px;
    -webkit-box-shadow: 0 0 18px -5px rgba(0,0,0,.25);
    box-shadow: 0 0 18px -5px rgba(0,0,0,.25);
    font-size: 22px;
    -webkit-transition: all .2s;
    -o-transition: .2s all;
    transition: all .2s;
  }

  input.validate {
    border-color: #F44336;
  }

  form button {
    position: absolute;
    top: 0;
    right: 0;
    background: #41b883;
    border: none;
    color: #fff;
    height: 100%;
    font-weight: 900;
    padding: 8px 30px;
    font-size: 28px;
    cursor: pointer;
  }

  .item-lists {
    list-style: none;
    padding: 0;
    margin: 0;
    margin-top: 25px;
    border: 1px solid #eee;
  }

  .item-lists li {
    position: relative;
    padding: 20px;
    width: 100%;
    border-bottom: 1px solid #eee;
  }

  .item-lists li:last-child {
    border-bottom: none;
  }

  .item-lists li span {
    width: 420px;
    height: 20px;
    font-size: 18px;
    text-align: left;
    font-weight: 300;
    display: inline-block;
    overflow: hidden;
  }

  .item-lists li span.done {
    color: #b0bec5;
    text-decoration: line-through;
  }

  .item-lists li button {
    position: absolute;
    top: 18px;
    right: 20px;
    background: #F44336;
    border: none;
    color: #fff;
    padding: 5px 10px;
    font-weight: 900;
    opacity: 0;
    cursor: pointer;
    -webkit-transition: all .2s;
    -o-transition: .2s all;
    transition: all .2s;
  }

  .item-lists li:hover button {
    opacity: 1;
  }
</style>
