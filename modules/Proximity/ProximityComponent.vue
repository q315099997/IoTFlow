<template>
    <el-select v-model="value" :placeholder="placeholder" @change="update()" size="small">
     <el-option
       v-for="item in values"
       :key="item.value"
       :label="item.value"
       :value="item.value">
     </el-option>
   </el-select>

</template>

<script>
export default {
  props: ['readonly', 'emitter', 'ikey', 'type', 'placeholder', 'that'],
   data() {
        return {
            value: 'HCSR04',
            values: [
              {
                value: 'HCSR04',
              },
              {
                value: 'GP2Y0A21YK',
              },
              {
                value: 'GP2Y0A710K0F',
              },
              {
                value: 'MB1230',
              }
            ]
        }
   },
  methods: {
       update() {
          if (this.ikey)
            this.that.putData(this.ikey, this.value)
            this.that.emitter.trigger('process');
      }
    },
    mounted() {
      this.value = this.that.getData(this.ikey);

    }
}
</script>
<style scoped>

</style>
