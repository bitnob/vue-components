<template>
    <div>

        <bitnob-textfield v-model="email" type="email" label="Email" icon=""></bitnob-textfield>

    </div>
</template>

<script lang="ts">

    import { Component, Vue } from 'vue-property-decorator';
    import { BitnobTextfield } from '@/components';

    @Component({
        components: { BitnobTextfield }
    })
    export default class App extends Vue {
        private email = '';
    }

</script>

<style lang="scss">

    * {
        box-sizing: border-box;
    }
    
    :root {
        --bitnob-background: white;

        --bitnob-primary: #4CAF50;
        --bitnob-secondary: green;
        --bitnob-font-family: 'Roboto', sans-serif;

        --bitnob-foreground: rgba(0, 0, 0, .72);
        --bitnob-foreground-secondary: rgba(0, 0, 0, .52);
        --bitnob-foreground-caption: rgba(0, 0, 0, .24);
        --bitnob-foreground-disabled: rgba(0, 0, 0, .24);
        --bitnob-divider: rgba(0, 0, 0, .12);

        --bitnob-transition-standard-easing: cubic-bezier(0.4, 0.0, 0.2, 1);
        --bitnob-transition-decelerate-easing: cubic-bezier(0.0, 0.0, 0.2, 1);
        --bitnob-transition-accelerate-easing: cubic-bezier(0.4, 0.0, 1, 1);

        --bitnob-transition-timing-fast: 0.25s;
        --bitnob-transition-timing-normal: 0.3s;
        --bitnob-transition-timing-slow: 0.35s;
    }

    html {
        font-size: 16px;
    }

</style>
