<script lang="ts">
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
        // console.log(event);
        if (event.key === "ArrowLeft") {
            console.log("arrow left")
        } else if (event.key === "ArrowRight") {
            console.log("arrow right")
        } else if (event.key === "ArrowUp") {
            console.log("arrow up")
        }
    }

    // Movement loop & logic.
    function updatePlayer() {

    }
</script>


<div class="player"></div>
<svelte:window on:keydown|preventDefault={onKeyDown} />

<style>
    .player {
        position: absolute;
        width: 100px;
        height: 100px;
        background-color: red;
        transform: translate();
    }
</style>