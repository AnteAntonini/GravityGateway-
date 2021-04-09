<template>
    <div>
        <h1>Master</h1>
        <iframe
        id="frameExample"
        title="Frame Example"
        src="http://localhost:8081/">
        </iframe>
        <button @click="msgToSlave">Send to Slave</button>
    </div>
</template>



<script>
import Gateway from '@nsoft/seven-gravity-gateway/master';


let master = Gateway({
    slaves : {
         GatewayPlayground: {
                frameId : 'frameExample',
                data : {
                    test: "hello from master",
                    mess: 'another message'
                },
                init: function() {
                },
                loaded: function() {
                    console.log('loaded event')
                    master.emit('frameExample', {
                        action : 'Betslip.Add',
                        data: {test: 'test123'},
                        slaveId : 'GatewayPlayground'
                    }, '*')
                }
         }
    },
    allowedOrigins : '*',
    debug : true,
})


master.on('helloMaster', (event) => console.log(event.data));


export default {
    name: 'Master',

    methods: {
        msgToSlave() {
            master.emit('frameExample', {
                action: 'helloSlave',
                data: {masterMessage: 'master message to slave'},
                slaveId: 'GatewayPlayground'
            }, '*')
        }
    }
}


</script>


<style scoped>
#frameExample {
    height: 500px !important;
    width: 500px;
}
</style>