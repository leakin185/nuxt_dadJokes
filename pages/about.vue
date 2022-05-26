<template> 
<div>
<h1> About DadJokes</h1> 
<p>This is an app that displays corny dad jokes</p> 
</div> 
</template>

<script>
export default {
    head(){ 
        return {
            title:'About The App', //this shows the title of the page in the header
            meta: [
                {
                    hid:"description",
                    name:"description",
                    content:"Best place for corny dad jokes" // SEO optimization, dynamics titles
                }
            ]
        }
    }
}
</script> 

<style> 
</style>