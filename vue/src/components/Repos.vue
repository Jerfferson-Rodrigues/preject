<template>
    <div class="card">
        <div class="row">
            <div class="text1">
                <div class="col1">
                    <a :href="repos.html_url" target="_blank" >{{repos.name}}</a>
                </div>
                <div class="card2">
                    <div><span class="cor">Star: {{ repos.stargazers_count }}</span></div>
                    <div><span class="cor">Watch: {{ repos.watchers_count }}</span></div>
                    <div><span class="cor">Forks: {{ repos.forks_count }} </span></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["repos"]
};
</script>

<style>

.row{
    text-align: center;
    margin: 10px;
    padding: 10px;
}

.card{
     max-width: 500px;  
  
}
.text1{
    background-color: black;
    padding: 20px;
    border-radius: 1px;
    box-shadow: 1px 1px 2px 1px #33ffd6;
    width: 250px;
    height: 100px;
}


</style>