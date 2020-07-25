<!DOCTYPE html>
<html lang="ko">
 
<head>
    <script src="https://www.youtube.com/embed/-BtHB-2rJwI" async></script>
    <style>
        html, body {
            padding: 0;
            margin: 0
        }

        .videoWrapper {
            position: fixed;
            top: 0;
            bottom: 0;
            left: 0;
            right: 0;
        }

        @media (min-aspect-ratio: 16/9) {
            .videoWrapper {
                height: 300%;
                top: -100%;
            }
        }

        @media (max-aspect-ratio: 16/9) {
            .videoWrapper {
                width: 300%;
                left: -100%;
            }
        }

        .videoWrapper iframe {
            position: absolute;
            top: 0;
            left: 0;
            width: 100%;
            height: 100%;
            pointer-events: none;
        }

    </style>
</head>
 
<body>
    <div class="videoWrapper" onclick="toggleSound()">
        <div id="player"></div>
    </div>
    <script>
        var tag = document.createElement('script');
        tag.src = 'https://www.youtube.com/embed/-BtHB-2rJwI';
        var firstScriptTag = document.getElementsByTagName('script')[0];
        firstScriptTag.parentNode.insertBefore(tag, firstScriptTag);
        var p;
 
        function onYouTubePlayerAPIReady() {
            p = new YT.Player('player', {
                height: '100%',
                width: '100%',
                playerVars: {
                    rel: 0,
                    playsinline: 1,
                    vq: 'hd1080',
                    autoplay: 1,
                    loop: 1,
                    playlist: 'rRzxEiBLQCA',
                    controls: 0,
                    autohide: 1,
                    showinfo: 0,
                    wmode: 'opaque'
                },
                videoId: 'rRzxEiBLQCA',
                events: {
                    onReady: onPlayerReady
                }
            })
        }
 
        function onPlayerReady(a) {
            a.target.playVideo(), a.target.mute()
        }
 
        function toggleSound() {
            p.isMuted() ? p.unMute() : p.mute()
        }
    </script>
</body>
 
</html>
