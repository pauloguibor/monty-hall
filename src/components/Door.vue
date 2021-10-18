<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <Gift v-if="open && hasGift"/>
        </div>
        <div class="door" :class="{ open }"
            @click="selected = !selected">
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div class="knob" :class="{ selected }"
            @click.stop="open = true"></div>
        </div>
    </div>
</template>

<script>
import Gift from './Gift'

export default {
    name: 'Door',
    components: {
        Gift
    },
    props:{
        number: {},
        hasGift: { type: Boolean }
    },
    data() {
        return {
            open: false,
            selected: false

        }
    }
}
</script>

<style>
    :root {
        --door-border:5px solid brown;
        --selected-border: 5px solid yellow
    }
    .door-area{
        position: relative;
        width: 200px;
        height: 310px;
        border-bottom: 10px solid #AAA;
        margin-bottom: 20px;
        font-size: 3rem;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .door-frame {
        position: absolute;
        height: 305px;
        width: 180px;

        border-left: var(--door-border);
        border-top: var(--door-border);
        border-right: var(--door-border);

        display: flex;
        justify-content: center;
        align-items: flex-end;
    }
    .door {
        position: absolute;
        top: 5px;
        height: 265px;
        width: 140px;
        background-color: chocolate;
        flex-direction: column;
        padding: 20px;
        align-items: center;
    }
    .knob {
        height: 20px;
        width: 20px;
        background-color: brown;
        border-radius: 50%;
        display: inline-block;
        margin-top: 60px;
        align-items: flex-end;
    }
    .door-frame.selected {
        border-left: var(--selected-border);
        border-top: var(--selected-border);
        border-right: var(--selected-border);
        
    }
    .door > .number.selected {
        color: yellow
    }

    .door > .knob.selected {
        background-color: yellow
    }
    .door.open {
        background-color: #0007;
    }
    .door.open .knob{
        display: none;
    }
    .door.open .number {
        display:none;
    }
</style>