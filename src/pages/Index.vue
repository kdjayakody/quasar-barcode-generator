<template>
<div class="q-pa-lg">
    <center class="q-mt-xl">
        <h1>KDJ QR Generator</h1>
        <q-input outlined v-model="barcodeValue" /><br>
        <barcode :value="barcodeValue" textPosition="bottom" height="50" width="1" textMargin="5" lineColor="black" format="CODE39" displayValue=TRUE>
            Enter Your Text and Happy QR
            <br>Powered By Quasar Framework
        </barcode>

    </center>

</div>
</template>

<script>
import VueBarcode from 'vue-barcode';
export default {
    data() {
        return {
            barcodeValue: ''
        }
    },
    components: {
        'barcode': VueBarcode
    }
}
</script>

<style>

</style>
