## VARIABLES

    $mobile-down : "screen and (max-width : 600px)";
    $mobile-up   : "screen and (min-width : 601px)";

    $tablet-down : "screen and (max-width : 767px)";
    $tablet-up   : "screen and (min-width : 768px)";

    $large-down : "screen and (max-width : 1365px)";
    $large-up   : "screen and (min-width : 1366px)";

    $touch-screen: "screen and (pointer: coarse) 

## USAGE

    @media #{$tablet-down} {
        height: 288px;
    }
    
    @media #($touch-screen) {
        display: none;
    }
