<main class="main-container">
    <section class="title-container">
        SPLI<br/>TTER
    </section>
    <section class="content-container">
        <div class="left-section"></div>
        <div class="right-section"></div>
    </section>
</main>

<style type="text/sass">
    $primary-color: hsl(172, 67%, 45%)
    $bg-content-color: hsl(185, 41%, 84%)
    $dark-input-text-color: hsl(186, 14%, 43%)
    $dark-input-text-disabled-color: hsl(184, 14%, 56%)
    $light-input-bg-color: hsl(189, 41%, 97%)
    $content-bg-color: hsl(0, 0%, 100%)
    $sub-content-bg-color-dark: hsl(183, 100%, 15%)

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
            font-weight: 500
        .content-container
            width: 64vw
            height: 47vh
            max-height: 700px
            display: grid
            border-radius: 20px
            overflow: hidden
            background-color: $content-bg-color
            justify-self: center
            align-self: center
            grid-template-columns: 1fr 1fr
                        

    @media only screen and (max-width: 500px)
        .main-container
            .content-container
                width: 100%
                height: 85vh
                max-height: min(600px, 100vh)

</style>