<template>
  <div class="card">
    <div class="row">
      <img src="../../img/driver.svg" alt="Avatar">
      <div class="message-container">
        <h1>Pedro</h1>
        <div class="message-text">
          <p>Hi, no problem see you later...</p>
          <span class="time-right">10:14</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
/* Chat containers */
.card {
  cursor: pointer;
  width: 100%;
  height: 180px;
  padding: 10px;
  font-family: Nunito;
  font-size: 24px;
  border: 1px solid white;
  /* White border */
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  z-index: 9998;
  color: white;
  /* Set text color to white */
}

.row {
  display: flex;
  align-items: center;
}

.card img {
  max-width: 60px;
  width: 100%;
  border-radius: 50%;
  margin: 10px;
}

.message-container {
  overflow: hidden;
}

h1 {
  font-size: 24px;
}

.message-text {
  display: flex;
  align-items: center;
  margin-top: 10px;
  margin-right: 16px;
  color: white;
}

.time-right {
  margin-left: 40px;
}
</style>