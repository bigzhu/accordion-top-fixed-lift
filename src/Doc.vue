<template>
  <div>
    <doc :name="name"
      :desc="desc"
      :parm_desc="parm_desc"
      :parms="parms"
      :code="code"
      >
      <bz :loading="loading" v-on:check_done="call_back"></bz>
    </doc>
  </div>
</template>
<script>
  import Bz from './Bz'
  import Doc from 'bz-doc'
  export default {
    components: {
      Bz,
      Doc
    },
    data: function () {
      return {
        loading: false,
        name: 'bz-base',
        desc: '顶',
        parms: [
          {parm: '', desc: ''}
        ],
        parm_desc: ``,
        code: `<bz></bz>`
      }
    },
    methods: {
    }
  }
</script>
