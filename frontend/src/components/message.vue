<template>
  <div class="card">
    <div class="row">
      <img src="../../img/driver.svg" alt="Avatar">
      <div class="message-content">
        <h1>Pedro</h1>
        <div class="message-info">
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

.card::after {
  content: "";
  clear: both;
  display: table;
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

.message-content {
  overflow: hidden;
}

.message-info {
  display: flex;
  align-items: center;
  margin-top: 10px;
}

.message-info p {
  margin-right: 10px;
}

.time-right {
  color: #aaa;
  margin-left: 40px;
}

p {
  color: white;
}
</style>
