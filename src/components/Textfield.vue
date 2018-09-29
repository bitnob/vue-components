<template>
    <div class="bitnob-textfield" :class="{ focused, hasText: value.length > 0 }">
        <div class="bitnob-textfield__label-cover">{{label}}</div>
        <label :for="label">{{label}}</label>
        <input
            @focus="onFocus"
            @blur="onBlur"
            @input="onInput"
            :id="label"
            :value="value" 
            :type="type" />
    </div>
</template>

<script lang="ts">

    import { Component, Vue, Prop } from 'vue-property-decorator';

    @Component({

    })
    export default class Textfield extends Vue {

        @Prop({ type: String, default: '' })
        public value: string;

        @Prop({ type: String, default: '' })
        public label: string;

        @Prop({ type: String, default: '' })
        public icon: string;

        @Prop({ type: String, default: '' })
        public type: string;

        public focused = false;

        private onInput(e) {
            this.$emit('input', e.target.value);
        }

        private onFocus() { this.focused = true; }
        private onBlur() { this.focused = false; }

    }

</script>

<style lang="scss">
    
    .bitnob-textfield {
        display: inline-flex;
        flex-direction: row;
        align-items: center;
        position: relative;

        font-family: var(--bitnob-font-family);
        font-size: 1rem;

        height: 3.5rem;
        border-radius: 3px;
        border: .125rem solid var(--bitnob-foreground);
        
        input {
            flex: 1;
            padding: 0.75rem;
            border: none;
            height: 100%;
            outline: none !important;
            box-shadow: none !important;
            background: transparent;
            font-family: inherit;
            font-size: inherit;
            color: var(--bitnob-foreground);
        }

        .bitnob-textfield__label-cover {
            background: var(--bitnob-textfield-label-background, var(--bitnob-background, white));
            font-size: 0.75rem;
            padding: 0 .25rem;
            height: .125rem;
            position: absolute;
            pointer-events: none;
            left: .5rem; top: -.125rem;
            color: transparent;

            will-change: transform;
            transform: scaleX(0);
            transition: transform var(--bitnob-transition-timing-fast) var(--bitnob-transition-standard-easing);
        }

        label {
            position: absolute;            
            left: 0.75rem;
            pointer-events: none;
            
            will-change: transform;
            transform-origin: center left;
            transition: transform var(--bitnob-transition-timing-fast) var(--bitnob-transition-standard-easing);
        }

        &.hasText,
        &.focused {
            label { transform: scale(0.75) translateY(-2.25rem); }
            .bitnob-textfield__label-cover { transform: scaleX(1); }
        }

        &.focused {
            border-color: var(--bitnob-primary);
            label { color: var(--bitnob-primary); }
        }

    }

</style>
