<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/aplayer/dist/APlayer.min.css">
<script src="https://cdn.jsdelivr.net/npm/aplayer/dist/APlayer.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/meting@2.0.1/dist/Meting.min.js"></script>

<div id="music-container">
    <meting-js
        server="netease" 
        type="playlist" 
        id="2195000539"> 
    </meting-js>
</div>

<style>
/* 让播放器居中显示的简单样式 */
.markdown-body {
    display: flex;
    flex-direction: column;
    align-items: center;
}
#music-container {
    width: 100%;
    max-width: 500px;
    margin-top: 50px;
}
</style>