<page>
    <actionBar title="Svelte Native App" />
    <stackLayout>
        <label>
            <formattedString>
            Set Start Count
            </formattedString>
        </label>
        <textField bind:text="{startCount}" on:returnPress={setStartCount}/>
        <label class="info" textWrap="true">
            <formattedString>
                <span class="fas" text="&#xf135;" />
                <span text=" {message}" />
                <span text="{count}"/>
            </formattedString>
        </label>
        <button class="counter" text="-" on:tap="{onButtonTap}" />
        <label>
            Remind allah atleast 30 minutes once
        </label>
        <label>
            Play audio
        </label>
        <button class="play_audio_btn" text="Play Audio" 
            on:tap="{playAudioBtn}" 
        />
    </stackLayout>
</page>

<script lang="typescript">
    import { TNSPlayer } from 'nativescript-audio-player';
    let message: string = "Allah Count: ";
    let startCount = 1000;
    let count = 1000;

    let player = new TNSPlayer();

    function playAudioBtn() {
        console.log("inside play audio button");
        player.initFromFile({
            audioFile: '~/audio/asma_ul_husna.mp3', // ~ = app directory
            loop: false,
            completeCallback: () =>{console.log("completed playing")},
            errorCallback: () => {console.log("error in playing")}
        })
        .then(() => {
            player.getAudioTrackDuration().then(duration => {
            // iOS: duration is in seconds
            // Android: duration is in milliseconds
            console.log(`song duration:`, duration);
            });
        });
    }
    function onButtonTap() {
        console.log("inside onButtonTap");
        if(count>0)
            count--;
    }
    function setStartCount() {
        console.log("inside setSTartCount ", startCount);
        count = startCount;
    }

    // setInterval(function(){ alert("Hello"); }, 3000);
</script>

<style>
    .info .fas {
        color: #3A53FF;
    }
    .info {
        font-size: 20;
    }
    .counter {
        width: 100%;
        background-color: goldenrod;
        font-size: 40;
    }
</style>
