<template>
    <div id="l-default">
        <header>
            <div id="header-container">
                <slot name="header"></slot>
            </div>
        </header>
        <main>
            <div id="main-container">
                <slot></slot>
            </div>
        </main>
        <footer>
            <div id="footer-container">
                <slot name="footer"></slot>
            </div>
        </footer>
    </div>
</template>

<script>
//Import and export all components here
</script>

<style lang="scss">

@import "../scss/variable/theme.scss";
@import "../scss/generics/typography.scss";

body{
  margin:0px;
  position:relative;
  background-color:$color4;
}

#app {
  font-family: $font;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#header-container, 
#main-container, 
#footer-container{
    max-width:$site-width;
    margin:0 auto;
    position:relative;
}

header{
    background-color: $color7;
    padding: 25px 50px;

    @media only screen and (max-width: 960px) {
        padding: 25px 20px;
        text-align: center;
    }
}

footer{
    background-color:$color2;
    padding-top: 80px;
    padding-bottom: 80px;
}

main{
    padding:0px;
    
}

</style>
