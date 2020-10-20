<template>
<div class="q-pr-xl q-pl-xl">
    <center class="q-mt-md">
        <h1>KDJ Barcode Generator</h1>
        <p class="text-left">Barcode Settings</p>

        <div class="row q-col-gutter-xs">
            <div class="col-4">
                <q-input filled v-model="options.lineColor" class="my-input">
                    <template v-slot:append>
                        <q-icon name="colorize" class="cursor-pointer">
                            <q-popup-proxy transition-show="scale" transition-hide="scale">
                                <q-color v-model="options.lineColor" />
                            </q-popup-proxy>
                        </q-icon>
                    </template>
                </q-input>
            </div>
            <div class="col-4">
                <q-input filled v-model="options.background" class="my-input">
                    <template v-slot:append>
                        <q-icon name="colorize" class="cursor-pointer">
                            <q-popup-proxy transition-show="scale" transition-hide="scale">
                                <q-color v-model="options.background" />
                            </q-popup-proxy>
                        </q-icon>
                    </template>
                </q-input>
            </div>

            <div class="col-1">
                <q-input label="Font Size" v-model.number="options.fontSize" type="number" filled style="max-width: 200px" />
            </div>
            <div class="col-1">
                <q-input label="Width" v-model.number="options.width" type="number" filled style="max-width: 200px" />
            </div>
            <div class="col-1">
                <q-input label="Height" v-model.number="options.height" type="number" filled style="max-width: 200px" />
            </div>
            <div class="col-1">
                <q-input label="Margin" v-model.number="options.margin" type="number" filled style="max-width: 200px" />
            </div>
        </div>
        <div class="barcode-container q-pt-lg">
            <q-input rounded outlined v-model="barcodeValue" placeholder="Item Code" /><br>
            <p>Barcode Result</p>
            <barcode :value="barcodeValue" :elementTag="tag" :background="options.background" :lineColor="options.lineColor" :fontSize="options.fontSize" :margin="options.margin" :width="options.width" :height="options.height">
            </barcode>
            <div v-if="barcodeValue">
                <button @click="downloadBarcode($event)">Download Now</button>
                <p class="q-pt-xs">If buttton didn't work, right click and save the image</p>
            </div>
        </div>

    </center>

</div>
</template>

<script>
import VueBarcode from 'vue-barcode';

export default {

    data() {
        return {

            barcodeValue: '',
            tag: 'canvas',
            options: {
                lineColor: '#ff7069',
                fontSize: 15,
                font: 'Courier',
                width: 1,
                height: 60,
                margin: 10,
                format: 'MSI',
                background: '#ffffff00'
            },
        }
    },
    components: {
        'barcode': VueBarcode
    },
    methods: {
        downloadBarcode(event) {
            var canvas = document.getElementsByClassName("vue-barcode-element");
            var image = canvas[0].toDataURL("image/png");
            console.log(image)
            event.href = image
        }
    }
}
</script>

<style lang="css" scoped>

</style>
