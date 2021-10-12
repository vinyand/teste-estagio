<template>
  <div style="height: 75vh; width: 50vw">
    <l-map v-model="zoom" v-model:zoom="zoom" :center="[-51.9252, -14.235]">
      <l-tile-layer
        url="https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png"
      ></l-tile-layer>
      <l-control-layers />
      <l-marker
        v-for="equipment in equipmentPosition"
        :key="equipment.equipmentId"
        :lat-lng="[equipment.positions[0].lat, equipment.positions[0].lon]"
      >
        <l-tooltip> estadoAtual </l-tooltip>
      </l-marker>
    </l-map>
  </div>
</template>

<script>
import {
  LMap,
  LTileLayer,
  LMarker,
  LControlLayers,
  LTooltip,
} from "@vue-leaflet/vue-leaflet";
import "leaflet/dist/leaflet.css";

import equipmentPosition from "../../data/equipmentPositionHistory.json";

export default {
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LControlLayers,
    LTooltip,
  },
  data() {
    return {
      zoom: 2,
      equipmentPosition,
    };
  },
};
</script>