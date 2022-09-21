<template>
    <div class="workspace">
    <h1>ABOUT THE PROJECT</h1>
    <p> This website is composed of a compilation of quizzes, users can compete as there is a visible leaderboard for each quiz,
        each time a person takes a quiz and finishes it the score is saved in Google Firestore.
    </p>
    <v-img width="50%" :src="require('@/assets/qna_about.png')"></v-img>
    <h1>PERSONAL INFORMATION ABOUT THE DEVELOPER</h1>
    <p> My name is Raphael Daniel Lazaro, a 4th year I.T. student in the Technological Institute of the Philippines
        - Manila. I currently reside in Parañaque city alongside my brother. My strongsuits are anything
        related to Photoshop and anything design-related in creating a web application or mobile
        application.
    </p>
    <v-img width="50%" :src="require('@/assets/aboutme.png')"></v-img>
    </div>
</template>

<script>
</script>

<style scoped>
.workspace h1{
    font-family: "Gotham Bold", Helvetica, Arial;
    font-weight: 500;
}
.workspace {
    font-family: "Gotham Medium", Helvetica, Arial;
    margin-right: 50%;
    padding-left: 5%;
    height: 100%;
    width: 100%;
    font-size: 20px;
}
</style>


