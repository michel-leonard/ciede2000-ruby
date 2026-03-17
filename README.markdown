# CIEDE2000 color difference formula in Ruby

This page presents the CIEDE2000 color difference, implemented in the Ruby programming language.

![Logo for CIEDE2000 in Ruby](https://raw.githubusercontent.com/michel-leonard/ciede2000-color-matching/refs/heads/main/docs/assets/images/logo.jpg)

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

## Public Domain Licence

You are free to use these files, even for commercial purposes.
