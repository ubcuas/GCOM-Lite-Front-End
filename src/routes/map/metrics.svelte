<!---------------->
<script>
    let mockdata = {
        velocity: 22.2,
        longitude: 49.2606,
        latitude: -123.246,
        altitude: 28.1111,
        heading: 11.2
    };

    let velocity = mockdata.velocity;
    let longitude = mockdata.longitude;
    let latitude = mockdata.latitude;
    let heading = mockdata.heading;
    let altitude = mockdata.altitude;
</script>

<head />

<!---------------->
<div class="metrics container">
    <h6 class="head text-center pt-2">Metrics</h6>
    <div class="figs text-center" style="margin-right: 1em;">
        <div class="row text-center">
            <div class="col">
                Velocity
                <p id="velocity">{velocity}</p>
            </div>
            <div class="col">
                Longitude
                <p class="Longitude">{longitude}</p>
            </div>
        </div>

        <div class="row text-center">
            <div class="col">
                Latitude
                <p class="latitude">{latitude}</p>
            </div>
            <div class="col">
                Altitude
                <p class="Altitude">{altitude}</p>
            </div>
        </div>

        <div class="row text-center">
            <div class="col">
                Heading
                <p class="heading">{heading}</p>
            </div>
            <div class="col">
                Yaw (Degree)
                <p class="yaw">0</p>
            </div>
        </div>
    </div>
</div>

<!---------------->
<style>
    .metrics {
        background-color: white;
        border-radius: 10px;
        margin-top: 0.75em;
        height: 50vh;
    }

    .head {
        font-size: 1.8em;
    }

    .row {
        margin-top: 1em;
        margin-left: 0.5em;
    }

    .figs {
        font-size: 1.2em;
    }

    p {
        color: #40b3ff;
    }

    .col {
        margin: 0;
        padding: 0;
    }
</style>
