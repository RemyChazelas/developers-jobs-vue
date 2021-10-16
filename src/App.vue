<template>
  <div class="app">
    <header>
      <div class="title">
        <img src="./assets/heart.png" alt="image of a heart with a symbol of my love to the code">
        <h1>Developers Jobs</h1>
      </div>
      <div class="order">
        <div class='btn' @click="handleClick('title')">Order by title</div>
        <div class='btn' @click="handleClick('salary')">Order by salary</div>
        <div class='btn' @click="handleClick('location')">Order by location</div>
      </div>
    </header>

    <JobList :jobs="jobs" :order="order" />
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from 'vue';
import Job from '@/types/Job'
import OrderTerm from '@/types/OrderTerm'
import JobList from './components/JobsList.vue'
export default defineComponent({
  name: 'App',
  components: { JobList },
  setup() {
    const jobs = ref<Job[]>([
      { title: 'Web Developers', location: 'Paris', salary: 50000, confidence:'Very high', desc: "Full stack developers understand how every part of the web development process takes place and can guide on strategy and best practices. These developers will have an increasingly important role in the web development of the future, and are able to look at the 'big picture'. They are knowledgeable with the server side as well as the client side’s user experience.", id: '1' },
      { title: 'Software Developers', location: 'Hong Kong', salary: 35000, confidence:'Very high', desc:'Software developers are the creative, brainstorming masterminds behind computer programs of all sorts. While some software developers may focus on a specific program or app, others create giant networks or underlying systems that help trigger and power other programs. This is why there are two main classifications of developers: applications software developers and systems software developers.', id: '2' },
      { title: 'Game Developers', location: 'New York', salary: 75000, confidence:'Very high', desc:'Video game developers work alone or in teams to write and program games for a variety of video game consoles. Read on to learn more about the many hats a game developer wears.', id: '3' },
      { title: 'Blockchain Developers', location: 'Anywhere', salary: 50000, confidence:'High', desc:'Blockchain developers enable secure digital transactions by creating systems to record and store blockchain data in a way that prevents changes or hacks. They design secure blockchain technologies, develop application features and interfaces, and maintain client and server-side applications.', id: '4' },
      { title: 'Mobile Developers', location: 'London', salary: 70000, confidence:'Very high', desc:'A mobile developer is responsible for translating code into user-friendly applications. They collaborate with internal teams to develop functional mobile applications while working in a fast-paced environment. ... Essentially, mobile developers contribute to the design, testing, releasing and support of the application.', id: '5' }
    ])
    const order = ref<OrderTerm>('title')
    const handleClick = (term: OrderTerm) => {
      order.value = term
    }
    return { jobs, order, handleClick }
  }
});
</script>

<style>
  header {
    text-align: center;
  }
  
  header .order {
    margin-top: 20px;
    display: flex;
    justify-content: center;
  }
  .title{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .title img{
    width: 50px;
    height: 50px;
    margin-right: 10px;
  }
  .title h1{
  text-decoration: underline 1.4px chartreuse;
  }
  .btn {
    margin: 0 10px;
    color: aliceblue;
    background: #262626;
    box-shadow:  2px 2px 0 #0f0f0f,
             -2px -2px 0 #2d2d2d;
    padding: 8px 10px;
    border-radius: 4px;
    cursor: pointer;
    font-family: "Roboto Mono", monospace;
    margin: 5px;
    letter-spacing: -0.5px;
    font-weight: 500;
  }
  .btn:hover {
    background: rgb(20, 20, 20);
    box-shadow: inset 2px 2px 1px #0f0f0f,
            inset -2px -2px 1px #2d2d2d;
  }
  @media (max-width: 500px) { 
    .btn {
    margin: 0 5px;    
    padding: 5px 8px;
    border-radius: 4px;
    margin: 5px;
    letter-spacing: -0.5px;
    font-size: 0.65rem;
  }
  
   }
</style>