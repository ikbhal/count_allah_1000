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
    </stackLayout>
</page>

<script lang="typescript">
    let message: string = "Allah Count: ";
    let startCount = 1000;
    let count = 1000;

    function onButtonTap() {
        console.log("inside onButtonTap");
        if(count>0)
            count--;
    }
    function setStartCount() {
        console.log("inside setSTartCount ", startCount);
        count = startCount;
    }
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
