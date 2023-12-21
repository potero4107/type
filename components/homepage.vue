<template>
    
    <div class="eeeverything_container h-screen w-full p-16 flex flex-col">
        <div class="everything_container h-full flex flex-col">
            <header>
                <div class="introtext_container pt-16">
                    <div class="introtext flex justify-center text-gray-600">a generative layered modular type</div>
                </div>
            </header>

            <div class="content_container m-auto h-full flex flex-col justify-evenly align-center mx-auto">
                <div class="values_container">
                    <div class="layertext_container flex justify-center text-gray-600">layer 1</div>
                    <div class="sliders_container">
                        <div class="slider_1_container">
                            <input type="range" min="0" max="1000" class="slider" id="slider1" v-model="slider1Value">
                        </div>
                        <div class="slider_2_container">
                            <input type="range" min="0" max="1000" class="slider" id="slider2" v-model="slider2Value">
                        </div>
                    </div>
                </div>

                <div class="display_text_container relative h-fit flex justify-center text-9xl p-8 mb-8 whitespace-nowrap">
                    <div class="text1_container absolute w-full top-0 right-80 mx-auto"
                        :style="textStyles('PIXER-MODULAR-VF', slider1Value, slider2Value)">PIXER MODULAR</div>
                    <div class="text2_container absolute w-full top-0 right-80 mx-auto"
                        :style="textStyles('PIXER-MODULAR-2-VF', slider3Value, slider4Value)">PIXER MODULAR</div>
                </div>

                <div class="values_container">
                    <div class="sliders_container">
                        <div class="slider_3_container pt-8">
                            <input type="range" min="0" max="1000" class="slider" id="slider3" v-model="slider3Value">
                        </div>
                        <div class="slider_4_container">
                            <input type="range" min="0" max="1000" class="slider" id="slider4" v-model="slider4Value">
                        </div>
                    </div>
                    <div class="layertext_container flex justify-center text-gray-600">layer 2</div>
                </div>

                <div class="button_container flex justify-center align-center hover:bg-gray-300 active:bg-black">
                    <button @click="randomizeValues" class="button border-3 text-black py-4 px-4">randomize!</button>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: "YourComponentName",
    data() {
        return {
            slider1Value: 0,
            slider2Value: 0,
            slider3Value: 0,
            slider4Value: 0,
        };
    },
    watch: {
        slider1Value: function (newValue) {
            this.updateSliderBackground(newValue, "slider1");
            this.updateTextStyles();
        },
        slider2Value: function (newValue) {
            this.updateSliderBackground(newValue, "slider2");
            this.updateTextStyles();
        },
        slider3Value: function (newValue) {
            this.updateSliderBackground(newValue, "slider3");
            this.updateTextStyles();
        },
        slider4Value: function (newValue) {
            this.updateSliderBackground(newValue, "slider4");
            this.updateTextStyles();
        },
    },
    methods: {
        updateSliderBackground(value, sliderId) {
            const slider = document.getElementById(sliderId);
            const percentage = ((value - slider.min) / (slider.max - slider.min)) * 100;
            slider.style.background = `linear-gradient(to right, #d9d9d9 ${percentage}%, #fff ${percentage}%)`;
        },
        textStyles(fontFamily, fontWeight, wdth) {
            return {
                fontFamily: fontFamily,
                fontWeight: fontWeight,
                fontVariationSettings: `"wght" ${fontWeight}, "wdth" ${wdth}`,
            };
        },

        updateTextStyles() {
            this.textStyles1 = this.textStyles('PIXER-MODULAR-VF', this.slider1Value, this.slider2Value, 'wdth');
            this.textStyles2 = this.textStyles('PIXER-MODULAR-2-VF', this.slider3Value, this.slider4Value, 'wdth');
        },

        randomizeValues() {
            // Genera valores aleatorios para wght y wdth
            const randomWght = Math.floor(Math.random() * 1000); // Puedes ajustar el rango según tus necesidades
            const randomWdth = Math.floor(Math.random() * 1000);

            // Asigna los valores aleatorios a las propiedades correspondientes
            this.slider1Value = randomWght;
            this.slider2Value = randomWdth;
            this.slider3Value = randomWght;
            this.slider4Value = randomWdth;

            // ... (repite el proceso para las propiedades de la segunda tipografía)

            // Actualiza los estilos del texto
            this.updateTextStyles();
        },

    },
};
</script>

<style scoped>
/* Estilos específicos del componente, si es necesario */
@font-face {
    font-family: "PIXER-MODULAR-VF";
    src: url("/assets/fonts/PIXER-MODULAR-VF.otf") format("opentype");
}

@font-face {
    font-family: "PIXER-MODULAR-2-VF";
    src: url("/assets/fonts/PIXER-MODULAR-2-VF.otf") format("opentype");
}

.slider {
    font-family: "PIXER-VARIABLE-VF";
    appearance: none;
    height: 20px;
    width: 100%;
    background: linear-gradient(to right, #d9d9d9 0%, #fff 0%);
    outline: none;
    margin: 10px 0;
    border: none;
    border-radius: 0;
}

.slider::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 20px;
    height: 20px;
    background: black;
    cursor: pointer;
    border-radius: 0;
}

.slider::-moz-range-thumb {
    width: 20px;
    height: 20px;
    background: black;
    cursor: pointer;
    border-radius: 0;
}

.text1_container {
    font-family: "PIXER-MODULAR-VF";
}

.text2_container {
    font-family: "PIXER-MODULAR-2-VF";
    /* Ajusta según el nombre de la segunda tipografía variable */
}

.introtext {
    font-family: "PIXER-MODULAR-VF";
}

.layertext_container {
    font-family: "PIXER-MODULAR-VF";
}

.button {
    font-family: "PIXER-MODULAR-VF";
}
</style>
