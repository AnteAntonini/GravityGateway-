<template>
  <div class="hello">
    <iframe id="frameExample"
    title="Frame Example"
    width="500"
    height="500"
    src="https://seven-integration-example.7platform.net/">
</iframe>

  </div>
</template>


<script>
import Gateway from '@nsoft/seven-gravity-gateway/slave';


let slave = Gateway({
    slaveId : 'GatewayPlayground',
    data : {test: "hello from slave"},
    allowedOrigins: '*',
    debug : false
});

slave.emit({
  action : 'Betslip.Add',
}, '*');


export default {
  name: 'Slave',
  data() {
    return {
    
    }
  }

}

</script>

<style>
.hello {
  display: flex;
  justify-content: center;
  margin-top: 40px;
  align-content: center;
  align-items: center;
}
</style>

