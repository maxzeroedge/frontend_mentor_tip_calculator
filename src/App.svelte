<script>
    let billAmount = "0";
    let tipAmount = "Custom";
    let peopleCount = "0"
    let tipPerson = "0"
    let amountPerson = "0"

    const tipOptions = [5, 10, 15, 25, 50]

    function inputFormatter(e) {
        let data = e.target.textContent
        if(!/^\d+$/ig.test(e.data)){
            data = data.replace(/\w+/ig, '')
        }
        
        if(!data) {
            data = "0"
        } else {
            data = parseFloat(data || "0").toFixed(2)
        }
        if(e.target.getAttribute("data-input-type") == "billAmount") {
            billAmount = data
        } else if (e.target.getAttribute("data-input-type") == "tipAmount") {
            tipAmount = data || "Custom"
        } else if (e.target.getAttribute("data-input-type") == "peopleCount") {
            peopleCount = data || "Custom"
        }
    }
</script>

<main class="main-container">
    <section class="title-container">
        SPLI<br/>TTER
    </section>
    <section class="content-container">
        <div class="left-section">
            <article class="article-container bill-input-container">
                <span class="bill-input-label label-style">Bill</span>
                <div class="bill-input">
                    <div class="input-prefix">$</div>
                    <div class="input-data" class:active={!!billAmount} 
                        data-input-type="billAmount"
                        contenteditable="true" 
                        bind:innerHTML="{billAmount}" 
                        on:blur={inputFormatter}
                    />
                </div>
            </article>
            <span class="bill-input-label label-style">Select Tip %</span>
            <article class="article-container tip-buttons-container">
                {#each tipOptions as tipOption}
                    <div class="tip-button-container button">
                        <span class="tip-amount">{tipOption}%</span>
                    </div>
                {/each}
                <div class="tip-button-container input-data" 
                    class:active={tipAmount && tipAmount!="Custom"} 
                    data-input-type="tipAmount"
                    contenteditable="true" 
                    bind:innerHTML="{tipAmount}" 
                    on:blur={inputFormatter}
                />
            </article>
            <span class="bill-input-label label-style">Number of People</span>
            <article class="article-container people-container bill-input-container">
                <div class="bill-input">
                    <div class="input-prefix">👤</div>
                    <div class="input-data" class:active={!!peopleCount} 
                        data-input-type="peopleCount"
                        contenteditable="true" 
                        bind:innerHTML="{peopleCount}" 
                        on:blur={inputFormatter}
                    />
                </div>
            </article>
        </div>
        <div class="right-section">
            <div class="result-container">
                <div class="amount-container">
                    <div class="amount-label">
                        <div class="amount-label-title">Tip Amount</div>
                        <div class="amount-label-subtitle">/ person</div>
                    </div>
                    <div class="amount-value">$ {tipPerson}</div>
                </div>
                <div class="amount-container">
                    <div class="amount-label">
                        <div class="amount-label-title">Total</div>
                        <div class="amount-label-subtitle">/ person</div>
                    </div>
                    <div class="amount-value">$ {amountPerson}</div>
                </div>
            </div>
        </div>
    </section>
</main>

<style type="text/sass">
    @import './vars.scss'

    .main-container
        width: 100vw
        height: 100vh
        display: grid
        justify-content: center
        align-content: center
        background-color: $bg-content-color
        color: $dark-input-text-color
        .title-container
            text-align: center
            padding-bottom: 5vh
            font-weight: bold
            letter-spacing: 0.5em
        .content-container
            width: 64vw
            height: 47vh
            min-height: 500px
            max-height: 700px
            display: grid
            border-radius: 20px
            overflow: hidden
            background-color: $content-bg-color
            justify-self: center
            align-self: center
            grid-template-columns: 1fr 1fr
            .left-section, .right-section
                padding: 50px
                box-sizing: border-box
                .label-style
                    font-size: 60%
                    font-weight: bold
                .article-container
                    margin-bottom: 32px
                .bill-input-container
                    //.bill-input-label
                    .bill-input
                        display: grid
                        grid-template-columns: 1em 1fr
                        padding: 2px 15px
                        border: solid 2px $primary-color
                        border-radius: 5px
                        align-content: center
                        background-color: $bg-color
                .input-prefix
                    text-align: left
                    padding: 3px
                    color: hsla(184, 14%, 56%, 50%)
                .input-data
                    text-align: right
                    outline: none
                    &.active
                        font-size: 120%
                        font-weight: bold
                        color: $sub-content-bg-color-dark
                .tip-buttons-container
                    display: grid
                    grid-template-columns: 1fr 1fr 1fr
                    grid-template-rows: 1fr 1fr
                    .tip-button-container
                        display: grid
                        align-content: center
                        justify-content: center
                        margin-top: 15px
                        border-radius: 5px
                        font-weight: bold
                        font-size: 110%
                        padding: 8px
                        &:nth-child(3n+2)
                            margin: 15px
                            margin-bottom: 0
                        &.button
                            background-color: $sub-content-bg-color-dark
                            color: $content-bg-color
                        &.input-data
                            border-radius: 5px
                            align-content: center
                            background-color: $bg-color
                            &.active, &::focus
                                border: solid 2px $primary-color
            .right-section
                .result-container
                    background-color: $sub-content-bg-color-dark
                    height: calc(100% - 50px)
                    border-radius: 20px
                    .amount-container
                        padding: 50px 50px 0
                        display: grid
                        grid-template-columns: 1fr 1fr
                        align-items: center
                        .amount-value
                            justify-self: flex-end
                        

    @media only screen and (max-width: 500px)
        .main-container
            .content-container
                width: 100%
                height: 85vh
                max-height: min(600px, 100vh)

</style>