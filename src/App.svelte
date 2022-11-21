<script lang="ts">
  import logo from "./assets/ICON.svg";

  document.addEventListener("mousemove", (e) => {
    const mouseX = e.clientX;
    const mouseY = e.clientY;

    const right = document.getElementById("btn-right");
    const rectRight = right.getBoundingClientRect();
    const rightX = rectRight.left + rectRight.width / 2;
    const rightY = rectRight.top + rectRight.height / 2;

    const angleRightDeg = angle(mouseX, mouseY, rightX, rightY);

    const arrowRight: HTMLElement = document.querySelector(".fa-arrow-right");

    arrowRight.style.transform = `rotate(${angleRightDeg * -1}deg)`;
    right.style.transform = `rotate(${angleRightDeg}deg)`;

    const left = document.getElementById("btn-left");
    const rectLeft = left.getBoundingClientRect();
    const leftX = rectLeft.left + rectLeft.width / 2;
    const leftY = rectLeft.top + rectLeft.height / 2;


    const angleLeftDeg = angle(mouseX, mouseY, leftX, leftY);

    const arrowLeft: HTMLElement = document.querySelector(".fa-arrow-left");

    arrowLeft.style.transform = `rotate(${angleLeftDeg * -1}deg)`;
    left.style.transform = `rotate(${angleLeftDeg}deg)`;
  });

  function angle(cx: number, cy: number, ex: number, ey: number) {
    const dy = ey - cy;
    const dx = ex - cx;

    const rad = Math.atan2(dy, dx);

    const deg = (rad * 180) / Math.PI;

    return deg;
  }
</script>

<main>
  <div id="btn-left" class="btn">
    <i class="fa-solid fa-arrow-left" />
  </div>
  <img class="logo" src={logo} alt="logo" />
  <div id="btn-right" class="btn">
    <i class="fa-solid fa-arrow-right" />
  </div>
</main>

<style>
  main {
    display: flex;
    flex-direction: row;
    align-items: center;
    background-color: black;
    height: 100vh;
    color: white;
    justify-content: space-around;
  }

  .btn {
    background-color: black;
    height: 100px;
    width: 100px;
    border-radius: 50%;
    box-shadow: 4px 0px 4px rgba(74, 74, 74, 25%);
    display: grid;
    place-items: center;
    font-size: 2rem;
  }

  .btn:nth-child(1) {
    /* visibility: hidden; */
    box-shadow: 4px 0px 4px rgba(74, 74, 74, 25%);
  }

  .btn:hover {
    cursor: pointer;
  }
  .btn:active {
    box-shadow: -0.2px 0.2px 4px rgba(74, 74, 74, 25%);
    transform: translate(-3px, 4px);
  }
  .btn:active:nth-child(1) {
    box-shadow: 0.2px -0.2px 4px rgba(74, 74, 74, 25%);
    transform: translate(4px, -3px);
  }

  .logo {
    height: 30vh;
    padding: 1.5em;
    will-change: filter;
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #ffffffaa);
    cursor: pointer;
  }
</style>
