<template>
    <div>
        <div class="mdc-switch"
             @click="toggle">
            <div class="mdc-switch__track"></div>
            <div class="mdc-switch__thumb-underlay">
                <div class="mdc-switch__thumb">
                    <input type="checkbox"
                           id="basic-switch" class="mdc-switch__native-control" role="switch">
                </div>
            </div>
        </div>
        <label for="basic-switch" class="margin-left-10">
            <slot></slot>
        </label>
    </div>
</template>

<script>
    import {MDCSwitch} from '@material/switch';

    export default {
        data: () => {
            return {
                state: false,
            }
        },
        props: {
            value: {
                type: Boolean,
                default: false
            },
            disabled: {
                type: Boolean,
                default: false
            },
        },
        methods: {
            toggle() {
                this.state = !this.state;
            },
        },
        watch: {
            state(val) {
                this.$emit('change', val);
                const switchControl = new MDCSwitch(this.$el.querySelector('.mdc-switch'));
                switchControl.getDefaultFoundation().setChecked(this.state);
            },
            value(val) {
                this.state = val;
            },
            disabled(val) {
                const switchControl = new MDCSwitch(this.$el.querySelector('.mdc-switch'));
                switchControl.getDefaultFoundation().setDisabled(val);
            }
        },
        model: {
            prop: 'value',
            event: 'change'
        },
        mounted() {
            this.state = this.value;
            const switchControl = new MDCSwitch(this.$el.querySelector('.mdc-switch'));
            switchControl.getDefaultFoundation().setChecked(this.state);
            switchControl.getDefaultFoundation().setDisabled(this.disabled);

        },
        name: "Switcher"
    }
</script>

<style scoped>
    @import "~@material/switch/dist/mdc.switch.min.css";

    .margin-left-10 {
        margin-left: 10px;
    }
</style>
