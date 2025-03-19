<template>
  <div class='box'>
    <div class='header'>
      <img src='/headers/avatar.gif' alt='Avatar' />
      <h3>「 arthur eleven 」</h3>
    </div>

    <div class='socials'>
      <a href='https://github.com/arthureleven'><img src='/socials/github.svg' alt='GitHub' /></a>
      <a href='https://anilist.co/user/arthureleven/'><img src='/socials/anilist.svg' alt='AniList' /></a>
      <a href='https://instagram.com/arthurcostv/'><img src='/socials/instagram.svg' alt='AniList' /></a>
    </div>
  </div>
</template>

<style scoped>
.box {
  align-items: center;
  background-color: black;
  border: 1px solid #ffffff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  padding: 45px;
  position: relative;
  text-align: center;
  transition: transform 0.2s ease-in-out;
  width: 300px;
}

.box:hover {
  transform: scale(1.01);
}

.header h3 {
  color: #ffffff;
  font-size: 1.35rem;
  margin: 10px 0 10px 0;
}

.header img {
  border-radius: 150px;
  height: 128px;
  margin: 10px 0 10px 0;
  object-fit: cover;
  width: 128px;
}

.header p {
  color: #ffffff;
  margin: 10px 0 10px 0;
}

.socials {
  margin: 10px 0 10px 0;
  width: 100%;
}

.socials a {
  margin-right: 10%;
}

.socials a:last-child {
  margin-right: 0;
}

.socials img {
  height: 40px;
  transition: all .3s;
  width: 40px;
}

.socials img:active {
  transform: scale(105%);
}

.socials img:hover {
  transform: scale(115%);
}
</style>