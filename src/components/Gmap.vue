<template>
 <div class="google-map" :id="mapName"></div>
 
</template>


<script>
export default {
    name: 'google-map',
    props: ['name'],
    data: function () {
        return {
            mapName: this.name + "-map",
            position: null,
            map: null,
            marker: null
        }
    },
    methods: {
        makeMap: function (coords) {
             //let myLatLng = {lat: -25.363, lng: 131.044};
             let myLatLng = coords;

            this.map = new google.maps.Map(document.getElementById(this.mapName), {
                zoom: 4,
                center: myLatLng
            });

            this.marker = new google.maps.Marker({
                position: myLatLng,
                map: this.map,
                title: 'Hello World!'
            });
        },
        print: function (message) {
            console.log(message);
        }
    },
    activated: function () {
        // const element = document.getElementById(this.mapName)
        if (navigator.geolocation) {
            navigator.geolocation.getCurrentPosition(function (position) {
                // let myLatLng = {
                //     let: position.coords.latitude,
                //     lg: position.coords.longitude
                // }
                //this.makeMap(myLatLng);
                this.position = position;
                // const options = {
                //     zoom: 14,
                //     center: new google.maps.LatLng(position.coords.latitude,position.coords.longitude)
                // } 
                // this.map = new google.maps.Map(element, options);
                // this.marker = new google.maps.Marker({
                //     position: options.center,
                //     title: 'Hello World!'
                // });
                // this.marker.setMap(this.map);
            });
        }

        let myLatLng = {lat: 38.435982, lng: -78.879997};

        this.map = new google.maps.Map(document.getElementById(this.mapName), {
            zoom: 14,
            center: myLatLng
        });

        this.marker = new google.maps.Marker({
            position: myLatLng,
            
            map: this.map,
            title: 'Hello World!'
        });
        
    }
    

};
</script>
<style scoped>
.google-map {
 width: 800px;
 height: 600px;
 margin: 0 auto;
 background: gray;
}
</style>
