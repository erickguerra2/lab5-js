# 🚀 Chat en JavaScript (Lab 5)

Este proyecto es un chat en tiempo real desarrollado en JavaScript puro, sin librerías externas. Se conecta al servidor [https://chat.nrywhite.lat/chats](https://chat.nrywhite.lat/chats) utilizando `GET` y `POST` para enviar y recibir mensajes.

## ✨ Características
- **Interfaz responsiva** para dispositivos móviles y escritorio.
- **Modo claro y oscuro**, con preferencia guardada en `localStorage`.
- **Campo de entrada fijo** en la parte inferior de la pantalla.
- **Límite de 140 caracteres** por mensaje.
- **Envío de mensajes con `Enter`**.
- **Actualización automática** de mensajes cada 5 segundos.
- **Previsualización de imágenes** en los mensajes.
- **Mantiene el scroll** después de recibir nuevos mensajes.
- **Código optimizado con `async/await` y deconstrucción de objetos**.

## 📦 Instalación y uso
1. Clona este repositorio:
   ```sh
   git clone https://github.com/erickguerra2/lab5-js.git
   ```
2. Abre el archivo `chat.html` en tu navegador.

## ⚙️ Funcionamiento
### **1. Obtener mensajes**
Se usa `fetch` con `async/await` para solicitar los mensajes al servidor:
```js
async function fetchMessages() {
    const response = await fetch("https://chat.nrywhite.lat/chats");
    const messages = await response.json();
    // Renderiza los mensajes en la pantalla
}
```
### **2. Enviar mensajes**
Los mensajes se envían por `POST`, asegurando que no excedan los 140 caracteres:
```js
async function sendMessage() {
    const text = inputField.value.trim();
    if (text.length === 0 || text.length > 140) return;
    
    await fetch("https://chat.nrywhite.lat/chats", {
        method: "POST",
        headers: { "Content-Type": "application/json" },
        body: JSON.stringify({ username: 3, message: text })
    });
    inputField.value = "";
    fetchMessages();
}
```
### **3. Cambio de tema**
Se guarda la preferencia del usuario en `localStorage`:
```js
themeButton.onclick = () => {
    const newTheme = localStorage.getItem("theme") === "dark" ? "light" : "dark";
    localStorage.setItem("theme", newTheme);
    location.reload();
};
```

## 🎨 Mejoras futuras
- Implementar **previsualización de enlaces web** en los mensajes.
- Añadir **animaciones** para mejorar la experiencia de usuario.

## 🛠 Tecnologías utilizadas
- **HTML5, CSS3 y JavaScript puro** (sin librerías externas)

