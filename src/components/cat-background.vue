<template>
    <div>
        <svg class xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" version="1.1" width="320" height="530">
            <filter id="grayscale">
                <feColorMatrix type="saturate" values="0.05"/>
                <feGaussianBlur stdDeviation="0.8" />
            </filter>
            <defs>
                <clipPath id="cp">
                    <polygon points="45,0 320,0 320,480 0,480 0,48"/>
                </clipPath>
                <clipPath id="cr">
                    <polygon points="0 0,70 0,40 0,0 42,0 70"/>
                </clipPath>
            </defs>
            <g class="svg__background" fill="white" stroke-width="4">
                <rect x="2" y="2" rx="14" fill="white" clip-path="url(#cp)" width="316" height="476" fill-opacity="1"/>
                <image x="4" y="0" xlink:href="../assets/card-layout.png" width="316" fill="white" height="478" />
                <foreignObject class="node" x="0" y="0" width="316" height="476">
                    <slot></slot>
                </foreignObject>

            </g>

            <g class="svg__background" fill="transparent" stroke="#2ea8e6" stroke-width="4">
                <rect x="2" y="2" rx="14" clip-path="url(#cr)" width="70" height="70" fill-opacity="0"/>

                <line x1="3" y1="48" x2="45" y2="2" opacity="0"/>
            </g>
        </svg>
    </div>

</template>

<script>
    export default {
        name: "cat-background",
    }
</script>

<style scoped>

</style>