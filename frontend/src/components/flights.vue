<template>
  <div>
    <div class="card-title">Ready for Takeoff! 🛫</div>
    <div class="card-container">
      <div class="card">
        <div class="card-content">
          <div class="card-header">Seville-Bologna</div>
          <div class="list">
            <div class="list-item">25.01</div>
            <div class="list-item">6:07</div>
          </div>
        </div>
      </div>

      <div class="card">
        <div class="card-content">
          <div class="card-header">Bologna-Seville</div>
          <div class="list">
            <div class="list-item">29.01</div>
            <div class="list-item">7:30</div>
          </div>
        </div>
      </div>
    </div>

    <div class="card-title">🏁 Successful Flights</div>
    <div class="card-container">
      <div class="card transparent">
        <div class="card-content">
          <div class="card-header">Zagreb-Charleroi</div>
          <div class="list">
            <div class="list-item">5.11</div>
            <div class="list-item">12:10</div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style>
.card {
  cursor: pointer;
  width: 100%;
  height: 200px;
  padding: 10px;
  font-family: Nunito;
  border: 1px solid white;
  /* White border */
  margin-top: 20px;
  margin-bottom: 20px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  z-index: 9998;
  color: white;
  /* Set text color to white */
}

.card-title {
  color: white;
  font-size: 24px;
  margin-top: 20px;
  margin-bottom: 20px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.card-content {
  font-family: 'Nunito';
  font-weight: normal;
  font-size: 24px;
  color: white;
  padding: 20px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.card-header {
  margin-bottom: 20px;
  text-align: center;
}

.list {
  display: flex;
}

.list-item {
  margin-right: 20px;
}

.pink {
  background: linear-gradient(135deg, #A690E0, #CFA7E8);
}

.bg-teal {
  background: linear-gradient(-45deg, #96B8FF, #CFA7E8);
}

.bg-blue {
  background-color: #96B8FF;
}

.transparent {
  opacity: 0.5;
}
</style>
