<!-- 1. The <iframe> (and video player) will replace this <div> tag. -->
<div id="player"></div>

<script>
  // 2. This code loads the IFrame Player API code asynchronously.
  var tag = document.createElement('script');

  tag.src = "https://www.youtube.com/iframe_api";
  var firstScriptTag = document.getElementsByTagName('script')[0];
  firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);

  // 3. This function creates an <iframe> (and YouTube player)
  //    after the API code downloads.
  var player;
  function onYouTubeIframeAPIReady() {
    player = new YT.Player('player', {
      height: '390',
      width: '640',
      videoId: '4JipHEz53sU',
      playerVars: {
        'start': 16,
        'end': 76
      },
      events: {
        'onReady': onPlayerReady
      }
    });
  }

  // 4. The API will call this function when the video player is ready.
  function onPlayerReady(event) {
    event.target.playVideo();
    event.target.cueVideoById({'videoId': 'bHQqvYy5KYo',
               'startSeconds': 5,
               'endSeconds': 60});
  }
</script>
