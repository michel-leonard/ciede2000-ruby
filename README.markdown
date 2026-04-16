Browse : [Microsoft Excel](https://github.com/michel-leonard/ciede2000-excel) · [PHP](https://github.com/michel-leonard/ciede2000-php) · [Perl](https://github.com/michel-leonard/ciede2000-perl) · [Python](https://github.com/michel-leonard/ciede2000-python) · [R](https://github.com/michel-leonard/ciede2000-r) · **Ruby** · [Rust](https://github.com/michel-leonard/ciede2000-rust) · [SQL](https://github.com/michel-leonard/ciede2000-sql) · [Swift](https://github.com/michel-leonard/ciede2000-swift) · [TypeScript](https://github.com/michel-leonard/ciede2000-typescript) · [VBA](https://github.com/michel-leonard/ciede2000-vba)

# CIEDE2000 color difference formula in Ruby

This page presents the CIEDE2000 color difference, implemented in the Ruby programming language.

![Logo for CIEDE2000 in Ruby](https://raw.githubusercontent.com/michel-leonard/ciede2000-color-matching/refs/heads/main/docs/assets/images/logo.jpg)

## About

Here you’ll find the first rigorously correct implementation of CIEDE2000 that doesn’t use any conversion between degrees and radians. Set parameter `canonical` to obtain results in line with your existing pipeline.

`canonical`|The algorithm operates...|
|:--:|-|
`false`|in accordance with the CIEDE2000 values currently used by many industry players|
`true`|in accordance with the CIEDE2000 values provided by [this](https://hajim.rochester.edu/ece/sites/gsharma/ciede2000/) academic MATLAB function|

## Our CIEDE2000 offer

This production-ready file, released in 2026, contain the CIEDE2000 algorithm.

Source File|Type|Bits|Purpose|Advantage|
|:--:|:--:|:--:|:--:|:--:|
[ciede2000.rb](./ciede2000.rb)|`Float`|64|General|Interoperability|

### Software Versions

- Ruby 1.X
- Ruby 2.X
- Ruby 3.X
- Ruby 4.X
- TruffleRuby 2X
- TruffleRuby 3X

### Example Usage

We calculate the CIEDE2000 distance between two colors, first without and then with parametric factors.

```ruby
# Example of two L*a*b* colors
l1, a1, b1 = 95.3, 58.8, 2.1
l2, a2, b2 = 95.7, 61.9, -1.7

delta_e = ciede2000(l1, a1, b1, l2, a2, b2)
puts "delta_e = #{delta_e}" # ΔE2000 = 1.940859230419468

# Example of parametric factors used in the dental industry
kl, kc, kh = 2.0, 1.0, 1.0

# Perform a CIEDE2000 calculation compliant with that of Gaurav Sharma
canonical = true

delta_e = ciede2000(l1, a1, b1, l2, a2, b2, kl, kc, kh, canonical)
puts "delta_e = #{delta_e}" # ΔE2000 = 1.929857865629
```

### Test Results

LEONARD’s tests are based on well-chosen L\*a\*b\* colors, with various parametric factors `kL`, `kC` and `kH`.

```
CIEDE2000 Verification Summary :
          Compliance : [ ] CANONICAL [X] SIMPLIFIED
  First Checked Line : 30.0,32.0,32.0,30.0,128.0,-127.4,1.0,1.0,1.0,45.32058741681242
           Precision : 12 decimal digits
           Successes : 100000000
               Error : 0
            Duration : 598.31 seconds
     Average Delta E : 67.12
   Average Deviation : 5e-15
   Maximum Deviation : 1.4e-13
```

```
CIEDE2000 Verification Summary :
          Compliance : [X] CANONICAL [ ] SIMPLIFIED
  First Checked Line : 30.0,32.0,32.0,30.0,128.0,-127.4,1.0,1.0,1.0,45.32039725637799
           Precision : 12 decimal digits
           Successes : 100000000
               Error : 0
            Duration : 596.54 seconds
     Average Delta E : 67.12
   Average Deviation : 5.5e-15
   Maximum Deviation : 1.4e-13
```

## Public Domain Licence

You are free to use these files, even for commercial purposes.
