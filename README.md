<!-- 1. The <iframe> (and video player) will replace this <div> tag. -->
<div id="player"></div>

<script>
  // 2. This code loads the IFrame Player API code asynchronously.
  var tag = document.createElement('script');

  tag.src = "https://www.youtube.com/iframe_api";
  var firstScriptTag = document.getElementsByTagName('script')[0];
  firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);
  
  class Song {
    constructor(id, end) {
      this.id = id;
      this.end = end;
      this.start = end - 60;
    }
  }

const songs = [
  new Song('4JipHEz53sU', 77), 
  new Song('wnJ6LuUFpMo', 110),
  new Song('dX3k_QDnzHE', 74),
  new Song('17ozSeGw-fY', 131),
  new Song('1ekZEVeXwek', 94)
];

  // 3. This function creates an <iframe> (and YouTube player)
  //    after the API code downloads.
  var player;
  var songIndex = 0;
  function onYouTubeIframeAPIReady() {
    const song = songs[songIndex++];
    player = new YT.Player('player', {
      height: '390',
      width: '640',
      videoId: song.id,
      playerVars: {
        'start': song.start,
        'end': song.end
      },
      events: {
        'onReady': onPlayerReady,
        'onStateChange': onPlayerStateChange
      }
    });
  }

  // 4. The API will call this function when the video player is ready.
  function onPlayerReady(event) {
    event.target.playVideo();
  }

  // 5. The API calls this function when the player's state changes.
  //    The function indicates that when playing a video (state=1),
  //    the player should play for six seconds and then stop.
  function onPlayerStateChange(event) {
    if (event.data == YT.PlayerState.ENDED) {
      const song = songs[songIndex++/2];
      player.loadVideoById({'videoId': song.id,
               'startSeconds': song.start,
               'endSeconds': song.end});
    }
  }

</script>
