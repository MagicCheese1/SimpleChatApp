<script>
  import Message from "./Message.svelte";
  import { onMount } from "svelte";

  let messages = [];
  let socket;

  onMount(() => {
    socket = new WebSocket("ws://localhost:8000/chat");
    socket.addEventListener("open", () => {
      console.log("Opened");
    });
  });

  function send_message() {}
</script>

<div class="wrapper">
  <div class="head">
    <h1>Simple Chat</h1>
    <div class="menu">
      <a class="ghbut" href="https://github.com/MagicCheese1"
        ><img src="github-mark-white.png" alt="Github" width="50px" /></a
      >
    </div>
  </div>
  <div class="messageWindow">
    <div class="messages">
      {#each messages as message}
        <Message
          author={message.author}
          timestamp={message.timestamp}
          messageText={message.message}
        />
      {/each}
    </div>
    <div class="inputwrapper">
      <input type="text" class="username someInput" placeholder="username" />
      <input type="text" class="MessageInput someInput" placeholder="message" />
      <button class="sendButton someInput">SEND</button>
    </div>
  </div>
</div>

<style>
  .wrapper {
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 100%;
  }
  .head {
    display: flex;
    justify-content: space-between;
  }
  .menu {
    padding: 15px;
  }
  .ghbut {
    background: none;
    border: none;
    cursor: pointer;
    overflow: hidden;
  }
  .messages {
    margin-left: 20px;
  }
  .inputwrapper {
    padding-top: 10px;
    display: flex;
    flex-direction: column;
    align-self: flex-end;
    margin: 0px 20px;
  }
  .someInput {
    height: 30px;
    border: none;
    margin: 5px 0px;
    border-radius: 5px;
    background-color: black;
  }

  .sendButton {
    background-color: gray;
    cursor: pointer;
  }
</style>
