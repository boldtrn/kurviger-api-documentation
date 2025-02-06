# Kurviger Api Documentation

Documentation of the motorcycle routing API of [Kurviger](https://kurviger.de/). The Kurviger API is offered as part of the GraphHopper directions API (more information can be found [here](https://kurviger.de/api_use) and [here](https://graphhopper.com/api/1/docs/supported-vehicle-profiles/)). The Kurviger API is perfectly suitable for you if you are looking for a motorcycle routing API. Kurviger is optimized to calculate routes that are fun to ride with a motorcycle and respects road rules for motorcyclists. If you would like to get access to the Kurviger API please contact either Kurviger or GraphHopper and we can set up access for you.

In most parts, the Kurviger API is similar to the GraphHopper API, which is documented [here](https://github.com/graphhopper/graphhopper/blob/master/docs/web/api-doc.md). This documentation will thererfore only cover the differences. 

If you are using the Kurviger API in your product, you need to make it clear that the service is provided by Kurviger. The attribution has to be shown on the same screen where you show the route - a user must have the possibility to read the attribution and click on the link. For example you can place the attribution on the map or an attached sidebar. Since Kurviger uses data from OpenStreetMap, you will have to show attribution for OpenStreetMap, as documented [here](https://www.openstreetmap.org/copyright). You can use this HTML for attributions:

```
Powered by <a href="https://kurviger.com">Kurviger</a>
```

**Note: this documentation contains all parameters that you are allowed to use when you have an active subscription. Kurviger contains some advanced options that are only allowed to use after receiving written permission.**

## Routing
Parameter   | Default       | Description
:-----------|:--------------|:-----------
vehicle     | [KURVIGER_VEHICLE]    | The vehicle for which the route should be calculated. Kurviger only offers motorcycle routing. We will send you the correct vehicle after you sign up for the api
weighting   | curvature     | Specifies the "road rating", you can choose between `fastest` which calculates the fastest route and `curvature`, which calculates a curvy and fun route optimized for motorcyclists.
elevation   | true   | If `true` a third dimension - the elevation - is included in the polyline or in the GeoJson. IMPORTANT: If enabled you have to use a modified version of the decoding method or set points_encoded to `false`. See the points_encoded attribute for more details.
additional_weighting |                  | Adds an additional weighting on top of your already choosen one. For roundtrips you should pass `avoid_edges` to reduce the chance of taking the same road twice. This will avoid taking the same road twice.
avoid_motorways      | false            | If set to `true`, motorways are avoided where possible
avoid_ferries        | false            | If set to `true`, ferries are avoided where possible
avoid_toll_roads     | false            | If set to `true`, toll roads are avoided.
ch.disable     | true            | In contrast to the GraphHopper routing API, Kurviger does not support CH. This means very long routes, or routes crossing continents might not be possible, please test this for your use case.

## Roundtrips

Parameter   | Default       | Description
:-----------|:--------------|:-----------
round_trip.distance        | 50000         | Specify the approximate length of a roundtrip in meter. The maximum distance is 300000 (300km/~186mi).
round_trip.seed            | 0            | Specify the seed of a roundtrip. The results of the calculation is always the same for the same seed. If you want random roundtrips, generate a random long and pass it.
heading    | -             | Specify the approximate heading a roundtrips should go to. The heading parameter is not only used for roundtrips, but also for routing itself. Very helpful when starting the navigating while driving, so we can make sure the route starts into the direction we are heading.