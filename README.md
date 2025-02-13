# Python Music with Sonic Pi

This repository contains various musical tunes created using Sonic Pi, a live coding music synthesizer. Each tune demonstrates different rhythmic and melodic patterns.

## Tunes

### Tune 1 - Basic Drum Beat
```ruby
live_loop :drums do
  sample :drum_heavy_kick
  sleep 1
end
```
A simple loop that plays a heavy kick drum every beat.

---

### Tune 2 - Basic Drum Pattern
```ruby
use_bpm 100

live_loop :drums do
  sample :drum_heavy_kick
  sleep 1
  sample :drum_snare_hard
  sleep 1
  sample :drum_heavy_kick
  sleep 1
  sample :drum_snare_hard
  sleep 1
end
```
A basic drum loop alternating between a kick and snare at 100 BPM.

---

### Tune 3 - Enhanced Drum Groove
```ruby
in_thread do
  live_loop :drums do
    sample :drum_bass_soft
    sleep 0.5
    sample :drum_stick
    sleep 0.25
    
    sample :drum_cymbal_closed
    sleep 0.5
    sample :drum_stick
    sleep 0.25
    
    with_fx :reverb do
      sample :drum_snare_soft
      sleep 0.5
      sample :drum_stick
      sleep 0.25
    end
    
    sample :drum_cymbal_closed
    sleep 0.5
    sample :drum_stick
    sleep 0.25
  end
end
```
This tune adds a stick sound and reverb for a more dynamic rhythm.

---

### Tune 4 - Fast-Paced Drum Groove
```ruby
in_thread do
  live_loop :drums do
    sample :drum_bass_soft
    sleep 0.25
    sample :drum_stick
    sleep 0.125
    
    sample :drum_cymbal_closed
    sleep 0.25
    sample :drum_stick
    sleep 0.125
    
    with_fx :reverb do
      sample :drum_snare_soft
      sleep 0.25
      sample :drum_stick
      sleep 0.125
    end
    
    sample :drum_cymbal_closed
    sleep 0.25
    sample :drum_stick
    sleep 0.125
  end
end
```
A fast drum sequence with shorter sleep intervals for a more energetic rhythm.

---

### Tune 5 - "Give Me Sunshine" Melody with Drums and Bass
```ruby
use_bpm 120

melody = [
  :e4, :g4, :a4, :b4, :a4, :g4, :e4, :d4,
  :e4, :g4, :a4, :b4, :a4, :g4, :e4, :d4,
  :c5, :b4, :a4, :g4, :f4, :e4, :d4, :e4,
  :g4, :a4, :b4, :a4, :g4, :e4, :d4, :e4
]

durations = [
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1
]

live_loop :give_me_sunshine do
  melody.each_with_index do |note, index|
    use_synth :saw
    play note, release: 0.8, amp: 0.7, attack: 0.2
    sleep durations[index]
    
    if index % 4 == 0
      in_thread do
        sample :drum_bass_soft, amp: 0.8
        sleep 0.25
        sample :drum_stick, amp: 0.6
        sleep 0.05
      end
      in_thread do
        use_synth :fm
        play :c2, release: 0.4, amp: 0.6
        sleep 0.5
      end
    end
  end
end
```
This tune plays a smooth and vibrant melody along with synchronized drum and bass patterns.

---

## How to Run These Tunes
1. Install [Sonic Pi](https://sonic-pi.net/).
2. Copy any of the above tunes into Sonic Pi.
3. Press the **Run** button to listen to the music.

Enjoy coding music! 🎵
