<script lang="ts">
	import { onMount } from "svelte";

    let playerX : number = 100; // Player's horizontal position.
    let playerY : number = 100; // Player's vertical position(starting on the floor).
    let velocityY : number = 0; // Player's vertical velocity for jumping and falling.
    const gravity : number = 0.5; // Gravity force.
    const speed : number = 5; // Player's horizontal speed.
    const jumpPower : number = 10; // Player's jumping strength.
    const groundLevel : number = 300; // Y Level of the floor.

    let isJumping  : boolean = false;
    let isGrounded  : boolean = false;

    // Movement controls (true if a key is pressed).
    let leftKeyPressed : boolean = false;
    let rightKeyPressed : boolean = false;
    let jumpKeyPressed : boolean = false;

    // Keyboard event listeners.
    function onKeyDown(event: KeyboardEvent) {
        console.log(event);
        if (event.key === "ArrowLeft") {
            leftKeyPressed = true;
            updatePlayer();
        } else if (event.key === "ArrowRight") {
            rightKeyPressed = true;
            updatePlayer();
        } else if (event.key === " ") {
            console.log("spacebar pressed.")
        }
    }

    function onKeyUp(event: KeyboardEvent) {
        if (event.key === "ArrowLeft") {
            leftKeyPressed = false;
            updatePlayer();
        } else if (event.key === "ArrowRight") {
            rightKeyPressed = false;
            updatePlayer();
        } else if (event.key === " ") {
            console.log("spacebar released.")
        }
    }

    // Movement loop & logic.
    function updatePlayer() {
        if ( leftKeyPressed ) {
            playerX -= speed;
            console.log(speed);
        } else if ( rightKeyPressed ) {
            playerX += speed;
            console.log(speed);
        }

        // requestAnimationFrame(updatePlayer); // Continue the loop.
    }

    onMount(() => {
        window.addEventListener('keydown', onKeyDown);
        window.addEventListener('keyup', onKeyUp);
        updatePlayer();
    });



</script>


<div class="player" style={`transform: translateX(${playerX}px) translateY(${playerY}px)`}></div>
<svelte:window on:keydown|preventDefault={onKeyDown} />

<style>
    .player {
        position: absolute;
        width: 100px;
        height: 100px;
        background-color: red;
    }
</style>