// ===== LOGIN SIMPLE PARA EL PANEL =====
function login() {
  const user = document.getElementById("username").value;
  const pass = document.getElementById("password").value;
  const errorMsg = document.getElementById("login-error");

  if (user === "OmenPrivado" && pass === "Ibce3406") {
    document.getElementById("login-section").style.display = "none";
    document.getElementById("admin-section").style.display = "block";
  } else {
    errorMsg.textContent = "❌ Usuario o contraseña incorrectos";
  }
}

// ===== AGREGAR NUEVOS PICKS AL PANEL =====
function addPick() {
  const match = document.getElementById("match").value;
  const pick = document.getElementById("pick").value;
  const odds = document.getElementById("odds").value;
  const analysis = document.getElementById("analysis").value;
  const video = document.getElementById("video").value;
  const success = document.getElementById("success-msg");

  if (!match || !pick || !odds || !analysis) {
    alert("Por favor completa todos los campos obligatorios.");
    return;
  }

  // Crear nueva fila en la tabla
  const table = document.getElementById("picks-table");
  const row = document.createElement("tr");

  row.innerHTML = `
    <td>${match}</td>
    <td>${pick}</td>
    <td>${odds}</td>
    <td>${analysis}</td>
    <td>${video ? `<a href="${video}" target="_blank">Ver video</a>` : '—'}</td>
  `;

  table.appendChild(row);

  // Limpiar formulario
  document.getElementById("match").value = "";
  document.getElementById("pick").value = "";
  document.getElementById("odds").value = "";
  document.getElementById("analysis").value = "";
  document.getElementById("video").value = "";

  success.textContent = "✅ Pick agregado correctamente";
  setTimeout(() => success.textContent = "", 3000);
}
