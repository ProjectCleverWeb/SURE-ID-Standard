# The SURE-ID Standard

The Simple Universal Reference Engine Identifier Standard

### What is it?

The <abbr title="Simple Universal Reference Engine Identifier">SURE-ID</abbr> standard aims to
provide unique, practical, and optimized identifiers that can be quickly generated without the need
for a central system to pull them from. This is similar to the
[UUID standard](https://en.wikipedia.org/wiki/Universally_unique_identifier) but differs on some key
areas such as flexibility, length, verification, and a focus on end-user readability.

### Features

- **Readable:** It is designed to be easily read by anyone by avoiding easily confused characters and having reasonable delimiters.
- **Flexible:** You can choose the variation that best fits your needs today and upgrade as needed
- **Upgradable:** Each variation of the standard is able to be easily upgraded to the next larger one. So you aren't locked into the variation you start with if you chose one that is too small.
- **Customizable:** 
- **Verifiable:** Each ID includes at least 1 check digit, allowing you to check for simple typos or miscommunications on the client-side
- **Randomized:** Guessing the next sequential ID is functionally-impossible at scale
- **Secure:** 
- **Non-Centralized:** IDs can be generated independent of each other without worrying about collisions<sup>**</sup>
- **Optimized:** IDs are not only designed to be generated quickly, but they can also be quickly looked up when dealing with an absurd amount of records. (Designed for storing even **trillions** of records)

<sup>**</sup> This technically cannot be guaranteed by **any** non-cenrtalized ID system, however it
is done "within reason". For example, you are about 1000 more likely to win the Powerball Lottery, get struck
by lightning, and then be attacked by a shark (roughly a 1 in 1.654x10<sup>19</sup> chance) than you
are to have a collision within the same second for SURE HC2. (roughly a 1 in 1.275x10<sup>22</sup> chance)

## Encoding

All parts of a SURE-ID are an integer that is encoded to a custom base 30 charset. Base 30 was
chosen specifically because it can be well balanced between not having easily confused characters
while also providing a significantly more dense key-space to work in.

The base 30 charset is defined as 0-9 followed by the uppercase alphabet, excluding the characters "BDIOQS" like so: `0123456789ACEFGHJKLMNPRTUVWXYZ`

## SURE-ID Parts Explained

The below explains how each part of a SURE-ID is generated BEFORE it is encoded to base30. The only
exceptions are the Tag and Check Digits. In both cases, base conversion is not viable.

### Tag

### Shard
The shard is defined as current epoch timestamp modulated by 20x30<sup>2</sup> (aka 18,000) and
adding 9,000 to the result. A shard will always start with a letter and will always be repeated
exactly 4 times a day, except on days containing leap-seconds.

A shard's primary purpose is optimization, but it does add a small a mount of key-space as well.
Specifically it adds 20x30<sup>2</sup> slots to the key-space, but is divided by 4 for variations
containing the date, and negated by variations containing the time.

### Date

The current UTC date represented as a concatenated base 10 integer, using only the last 2 digits of
a year. As a result, the date `2024-12-31` becomes `241231` and the date `3000-01-01` becomes `101`.

**Known Limitation:** This means that dates are reused after every 100 years. This is considered the
system administrators problem as it means you are retaining tracking data well beyond its usefulness.

### Time

The current UTC time of day represented as a concatenated base 10 integer. As a result, the time
`23:59:59` becomes `235959` and the time `00:00:00` becomes `0`.

### Subtime



### RNG
### Check Digits



## Variations

Each of the variations below 

### Random Only
**SURE R1:** MN5-1YHCM-2 (Need < 800,000 IDs ever)<br>
**SURE R2:** MN5-5AY49-1YHCM-2 (Need < 4 billion IDs ever)<br>

### Continuous
**SURE C1:** N3N-08XJP-U152Y-1 (Need < 500,000 IDs per day)<br>
**SURE C2:** N3N-08XJP-5KYC-U152Y-1 (Need < 500,000 IDs per second)<br>

### High-Concurrency
**SURE HC1:** N3N-08XJP-5KYC-0ZF-U152Y-1 (Need < 500,000 IDs per millisecond)<br>
**SURE HC2:** N3N-08XJP-5KYC-0ZF-57243-U152Y-0 (Need < 24 million IDs per millisecond)<br>

### Hexadecimal
**SURE HEX:** 6977f1fff39e0e3e7172c9df172c9df0<br>

### Tags
OBJECT/MN5-1YHCM-2<br>
OBJECT/MN5-2AW83AL-1YHCM-5<br>
OBJECT/-MN5-2AW83AL-0XJ-5AY49-1YHCM-25890<br>


Exclude: BDIOQS

tag/.shard.timestamp.millisecond.rng1.rng2.check

.MN5.2AW83AL.0XJ.5AY49.1YHCM.25890<br>
-MN5-2AW83AL-0XJ-5AY49-1YHCM-25890<br>
_MN5_2AW83AL_0XJ_5AY49_1YHCM_25890

~MN52AW83AL0XJ5AY491YHCM25890

### Randomized
**SURE R1:** MN5-1YHCM-2 (Need < 800,000 IDs ever)<br>
**SURE R2:** MN5-5AY49-1YHCM-2 (Need < 4 billion IDs ever)<br>

### Continuous
**SURE C1:** N3N-08XJP-U152Y-1 (Need < 500,000 IDs per day)<br>
**SURE C2:** N3N-08XJP-5KYC-U152Y-1 (Need < 500,000 IDs per second)<br>

### High-Concurrency
**SURE HC1:** N3N-08XJP-5KYC-0ZF-U152Y-1 (Need < 500,000 IDs per millisecond)<br>
**SURE HC2:** N3N-08XJP-5KYC-0ZF-57243-U152Y-0 (Need < 24 million IDs per millisecond)<br>

### Hex
**SURE HEX:** 6977f1fff39e0e3e7172c9df172c9df0<br>

### Tags
OBJECT/MN5-1YHCM-2<br>
OBJECT/MN5-2AW83AL-1YHCM-5<br>
OBJECT/-MN5-2AW83AL-0XJ-5AY49-1YHCM-25890<br>

10,628,820,000,000,000,000


# License

THIS LICENSE ONLY APPLIES TO THIS STANDARD ITSELF AND NOT ANY CODE PRODUCED FOR THE STANDARD

<p xmlns:cc="http://creativecommons.org/ns#" xmlns:dct="http://purl.org/dc/terms/"><a property="dct:title" rel="cc:attributionURL" href="https://github.com/ProjectCleverWeb/SURE-ID-Standard">The SURE-ID Standard</a> by <a rel="cc:attributionURL dct:creator" property="cc:attributionName" href="https://github.com/ProjectCleverWeb">Nicholas Summers</a> is licensed under <a href="https://creativecommons.org/licenses/by-nd/4.0/?ref=chooser-v1" target="_blank" rel="license noopener noreferrer" style="display:inline-block;">CC BY-ND 4.0<img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/cc.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/by.svg?ref=chooser-v1" alt=""><img style="height:22px!important;margin-left:3px;vertical-align:text-bottom;" src="https://mirrors.creativecommons.org/presskit/icons/nd.svg?ref=chooser-v1" alt=""></a></p>
