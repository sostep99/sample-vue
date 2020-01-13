<template>
 <div class="google-map" :id="mapName"></div>
 
</template>


<script>
export default {
    // creates the map
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

        print: function (message) {
            console.log(message);
        },

        // Function for calculating best route
        calcRoute: function (origin, destination) {
            this.createMap();
            var directionsService = new google.maps.DirectionsService();
            var directionsRenderer = new google.maps.DirectionsRenderer();
            directionsRenderer.setMap(this.map);
            var request = {
                origin: new google.maps.LatLng(origin.lat, origin.long),
                destination: new google.maps.LatLng(destination.lat, destination.long),
                travelMode: 'DRIVING'
            };
            directionsService.route(request, function(result, status) {
                if (status == 'OK') {
                    directionsRenderer.setDirections(result);
                } else {
                    console.log("Route failed!")
                }
            });
        },
        createMap: function () {
         // Finds your location stores in this.position
        // if (navigator.geolocation) {
        //     navigator.geolocation.getCurrentPosition(function (position) {
        //         this.position = position;
        //     });
        // }


        // this.position not working so set place holder coords instead stored im mylatlng
        let myLatLng = {lat: 38.435982, lng: -78.879997};

        // centers map at mylatlg
         this.map = new google.maps.Map(document.getElementById(this.mapName), {
            zoom: 14,
            center: myLatLng
        });
        }
    },
    activated: function () {
        this.createMap();
    },
    
    
    

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
