<page>
    <actionBar title="Svelte Native App" />
    <gridLayout>
        <label class="info" horizontalAlignment="center" verticalAlignment="middle" textWrap="true">
            <formattedString>
                <span class="fas" text="&#xf135;" />
                <span text=" {message}" />
                <span text="{count}"/>
            </formattedString>
            <!-- <button text="Count" on:tap="{onButtonTap}" /><br/> -->
            <!-- <div>Allah Count {count}</div> -->
            <!-- <div>{count}</div> -->


        </label>

        <button class="counter" text="+" on:tap="{onButtonTap}"
            horizontalAlignment="center" verticalAlignment="bottom"    
        />

    </gridLayout>
</page>

<script lang="typescript">
    let message: string = "Allah Count: ";
    let count = 0;

    function onButtonTap() {
        console.log("inside onButtonTap");
        count++;
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
