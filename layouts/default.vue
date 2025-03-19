<template>
  <Background />
  <main>
    <slot />
  </main>
</template>

<style>
body {
  background-color: #000000;
  cursor: url(https://cur.cursors-4u.net/nature/nat-11/nat1034.ani), url(https://cur.cursors-4u.net/nature/nat-11/nat1034.gif), auto !important;
  margin: 0;
  padding: 0;
  font-family: 'IBM Plex Mono', monospace;
}

main {
  align-items: center;
  display: flex;
  justify-content: center;
  min-height: 100vh;
  text-align: center;
}

canvas {
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
}
</style>