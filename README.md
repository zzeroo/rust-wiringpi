#WiringPi Bindings for Rust

An API wrapper for [WiringPi](http://wiringpi.com/) to make it accessible
using Rust. It implements the most important functions and provides a bit of
type system convenience.

[Online documentation](http://ogeon.github.io/docs/rust-wiringpi/master/wiringpi/index.html)

Add the following lines to your `Cargo.io` to use `rust-wiringpi`:

```
[dependencies]
wiringpi = "0.1"
```

or add these lines to opt in to Rust-nightly features:

```
[dependencies.wiringpi]
verson = "0.1"
features = ["nightly"]
```

##Example: Flashing Light

```Rust
extern crate wiringpi;

use wiringpi::pin::Value::{High, Low};
use wiringpi::time::delay;

fn main() {
    //Setup WiringPi with its own pin numbering order
    let pi = wiringpi::setup();

    //Use WiringPi pin 0 as output
    let pin = pi.output_pin(0);

    loop {
        //Set pin 0 to high and wait one second
        pin.digital_write(High);
        delay(1000);

        //Set pin 0 to low and wait one second
        pin.digital_write(Low);
        delay(1000);
    }
}
```

##Cross Compiling Using Cargo

This project can be cross compiled using Cargo.
[Follow these instructions](https://github.com/Ogeon/rust-on-raspberry-pi)
And use `./cross64 build` or `./cross32 build`, depending on your system,
to check if everything builds as expected.
