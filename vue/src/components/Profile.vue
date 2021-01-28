<template>
    <div>
        <div class="row">
            <div class="col-md">
                <div class="card" style="width : 18rem">
                    <img class="img" :src="user.avatar_url"/>
                    <ul>
                        <li class="list">
                            Repositorios: <span class="badge">{{ user.public_repos }}</span>
                        </li>
                        <li class="list">
                            Seguidores: <span class="badge">{{ user.followers }}</span>
                        </li>
                        <li class="list">
                            Seguindo: <span class="badge">{{ user.following }}</span>
                        </li>
                    </ul>
                    <div class="card1">
                        <a :href="user.html_url"> Ver perfil</a>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ["user"]
};
</script>

<style>
body,html{
    background-color: #2d3039;
}
.card{
    margin: 0 auto;
    text-align: center;
    color: white;
}
.list{
    list-style: none;
    margin: 10px;   
    text-align: center;
}
 .card1{
    text-align: center;
    background-color: #141414;
    margin-left: 90px;
    margin-right: 90px;
    padding: 5px;
    font-size: 15px;
    border-radius: 9px;
    color: cyan;
} 
a{
    text-decoration: none;
    color: #33ffd6;   
}
.img{
    width: 200px;
}
</style>