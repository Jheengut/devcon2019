<template>
  <div class="container">
    <h1 class="mega-rainbow">Convince my boss</h1>

    <div class="full-section-container">
        <div class="section-title-wrapper">
            <small>Need some help for a writeup to convince your boss that you should attend our awesome conference?</small>
            <small>Enter the name and move the slider !</small>
<br>
<br>
        </div>
        <div class="section-description-wrapper">
            <div class="fields">
                <div class="field-wrapper">
                    <label for="">What's the name of your boss?</label>
                    <input type="text" v-model="bossname">
                </div>

                <div class="field-wrapper">
                    <label for="">How grumpy is your boss?</label>
                    <input type="range" class="range-slider" v-model="level" min="1" :max="maxContent">
                </div>
            </div>
        
            <div class="letter">

                <p>Hello {{ bossname }}</p>

                <transition-group name="fade" tag="div">
                    <p v-for="(paragraph) in contentOut" :key="paragraph" v-html="paragraph"></p>
                </transition-group>

                <p class="bold">Thank you for getting back to me on this subject.</p>
            </div>

                    <div class="section-title-wrapper">
<br>
            <small>Now you can copy-paste this and hope for the best !</small>
<br>
        </div>

        </div>
    </div>
  </div>
</template>


<script>
export default {
    data() {
        return{ 
            bossname: "Mr Fromage",
            level: 1,
            content: [
                "As you may know, the annual developers conference will be held this 11th of April to the 13th and I would love to attend the event.",
                "It would be very enriching to be able to attend the sessions which interest me and that will help at work.",
                "We get to learn new technologies that's being used for different codebase.",
                "We learn about the different project methodologies being used by other companies.",
                "We get a lot more enthusiastic and focused by meeting and sharing thoughts with other developers.",
                "Sometimes there are workshops which allow us to get an idea on things we didnt know about before.",
                "It is a way of investing in your employees and sharpening them.",
                "Listen if you're still not convinced, your cat might dissapear."
            ]

        }
    },
    computed: {
        maxContent() {
            return this.content.length;
        },
        contentOut() {
            return this.content.slice(0, this.level)
        }
    }
}
</script>


<style lang="scss" scoped>

    .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
    }
    .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
    }

    .section-title-wrapper{
        text-align: center;
    }

    .fields {
        text-align: center;
        display:grid;
        grid-template-columns: 1fr 1fr;
        grid-gap: 40px;
        justify-content: center;
        padding: 20px 0;
        max-width: 600px;
        width: 100%;
        margin: 0 auto;
    }

    .field-wrapper {
        display:block;
    }
    label {
        color:white;
        display: block;
        padding-bottom: 10px;
    }

    .letter {
        background:rgba(255,255,255,0.5);
        border:10px dashed white;
        padding: 40px;
    }


    .range-slider {
    -webkit-appearance: none;
    width: 100%;
    height: 10px;
    border-radius: 5px;
    background: #d7dcdf;
    outline: none;
    padding: 0;
    margin: 0;
    }

    .low.range-slider{
    background: #f5c8c8;
    }
    .high.range-slider{
    background: #b6d2b9;
    }

    .range-slider::-webkit-slider-thumb {
    -webkit-appearance: none;
            appearance: none;
    width: 20px;
    height: 20px;
    border-radius: 50%;
    background: #ff4932;
    cursor: pointer;
    -webkit-transition: background .15s ease-in-out;
    transition: background .15s ease-in-out;
    }


    /* .range-slider::-webkit-slider-thumb:hover,
    .range-slider:active::-webkit-slider-thumb {
    background: #1abc9c;
    } */

    .range-slider::-moz-range-thumb {
    width: 20px;
    height: 20px;
    border: 0;
    border-radius: 50%;
    background: #2c3e50;
    cursor: pointer;
    -webkit-transition: background .15s ease-in-out;
    transition: background .15s ease-in-out;
    }

    /* .range-slider::-moz-range-thumb:hover,
    .range-slider:active::-moz-range-thumb {
    background: #1abc9c;
    } */


    .range-slider::-webkit-slider-thumb:hover,
    .range-slider:active::-webkit-slider-thumb {
    background: #ff4932;
    width: 30px;
    height: 30px;
    }

    .range-slider::-moz-range-thumb:hover,
    .range-slider:active::-moz-range-thumb {
    background: #ff4932;
    width: 30px;
    height: 30px;
    }

    .low::-webkit-slider-thumb:hover,
    .low:active::-webkit-slider-thumb {
    background: red;
    }

    .high::-webkit-slider-thumb:hover,
    .high:active::-webkit-slider-thumb {
    background: #1abc9c;
    }

    ::-moz-range-track {
    background: #d7dcdf;
    border: 0;
    }

    input::-moz-focus-inner,
    input::-moz-focus-outer {
    border: 0;
    }

</style>
