<script>
  export let author = "Rudy";
  export let timestamp = "02:00";
  export let messageText = "Kupa";
</script>

<div class="wrapper">
  <div class="MessageHeader">
    <div class="author">{author}</div>
    <div class="timestamp">{timestamp}</div>
  </div>
  <div class="MessageContent">{messageText}</div>
</div>

<style>
  .MessageHeader {
    display: flex;
    flex-direction: row;
  }
  .author {
    font-weight: bold;
    padding-right: 5px;
  }
  .timestamp {
    font-weight: lighter;
    color: slategrey;
  }
  .wrapper {
    padding: 2px 0px;
  }
</style>
