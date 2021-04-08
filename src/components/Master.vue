<template>
    <div>
        <h1>Master</h1>
        <iframe
        id="frameExample"
        title="Frame Example"
        width="700"
        height="500"
        src="http://localhost:8081/">
        </iframe>
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
                init: function(data) {
                    console.log('initialized master', data)
                },
                loaded:  function() {
                    console.log('loaded event')
                }
         }
    },
    allowedOrigins : '*',
    debug : false,
})

master.on("HelloMaster", (event) => console.log(event.data.message));

master.emit('frameExample', {
    action : 'Betslip.Add',
    data: {test: 'test123'},
    slaveId : 'GatewayPlayground'
}, '*')




export default {
    name: 'Master',
}

</script>
