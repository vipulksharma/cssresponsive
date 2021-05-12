# cssresponsive

Open sass to css online compiler if sass not avaiable: https://jsonformatter.org/sass-to-css#save

SASS:

$breakpoints: (
  'extrasmall': ( min-width: 200px),
  'small':  ( min-width:  600px ),
  'medium': ( min-width:  992px ),
  'large':  ( min-width: 1200px )
) !default;

@mixin respond-to($breakpoint) {
  // If the key exists in the map
  @if map-has-key($breakpoints, $breakpoint) {
    // Prints a media query based on the value
    @media #{inspect(map-get($breakpoints, $breakpoint))} {
      @content;
    }
  }
 
  // If the key doesn't exist in the map
  @else {
    @warn "Unfortunately, no value could be retrieved from `#{$breakpoint}`. "
        + "Available breakpoints are: #{map-keys($breakpoints)}.";
  }
}

// Usage as below. Write code for mobile and responsive using response to.

p {
    color: yellow;
  
  @include respond-to('small') {
    color: blue;
  }
  @include respond-to('medium') {
    color: red;
  }
  @include respond-to('large') {
    color: green;
  }
  
}


