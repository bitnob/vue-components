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
        font-size: 16px;

        height: 56px;
        border-radius: 3px;
        border: 2px solid var(--bitnob-foreground);
        
        input {
            flex: 1;
            padding: 12px;
            border: none;
            height: 100%;
            outline: none !important;
            box-shadow: none !important;
            background: transparent;
            font-family: inherit;
            font-size: inherit;
        }

        .bitnob-textfield__label-cover {
            background: var(--bitnob-textfield-label-background, var(--bitnob-background, white));
            font-size: 12px;
            padding: 0 4px;
            height: 3px;
            position: absolute;
            pointer-events: none;
            left: 8px; top: -3px;
            color: transparent;
            transform: scaleX(0);
            transition: transform var(--bitnob-transition-timing-fast) var(--bitnob-transition-standard-easing);
        }

        label {
            position: absolute;            
            left: 12px;
            pointer-events: none;
            
            transform-origin: center left;
            transition: transform var(--bitnob-transition-timing-fast) var(--bitnob-transition-standard-easing);
        }

        &.hasText,
        &.focused {
            label { transform: scale(0.75) translateY(-35px); }
            .bitnob-textfield__label-cover { transform: scaleX(1); }
        }

        &.focused {
            border-color: var(--bitnob-primary);
            label { color: var(--bitnob-primary); }
        }

    }

</style>
