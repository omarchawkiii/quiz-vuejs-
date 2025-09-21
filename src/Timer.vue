<template>
    <div>
        Time : {{ time }}
        <hr />
        largeur : {{ size.width }} <br >
        hauteur  : {{ size.height }}
    </div>
</template>

<script setup>

    import {ref, onMounted, onUnmounted} from 'vue' ; 
    const time = ref(0)
    const size = ref({
        width: 0,
        height: 0
    })
    let timer ; 
    onMounted(() => {
        
        timer = setInterval(() => {
            time.value++; 
            console.log('timer')
        }, 1000);
        
    })

    onUnmounted(() => {
        clearInterval(timer)
    })


    
</script>