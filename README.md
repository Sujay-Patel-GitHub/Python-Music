# Python-Music

tune 1

live_loop :drums do
  sample :drum_heavy_kick
  sleep 1
end



tune 2


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



tune 3

in_thread do
  live_loop :drums do
    sample :drum_bass_soft
    sleep 0.5
    sample :drum_stick  # Added stick sound after bass drum
    sleep 0.25
    
    sample :drum_cymbal_closed
    sleep 0.5
    sample :drum_stick  # Added stick sound after closed cymbal
    sleep 0.25
    
    with_fx :reverb do
      sample :drum_snare_soft
      sleep 0.5
      sample :drum_stick  # Added stick sound after snare
      sleep 0.25
    end
    
    sample :drum_cymbal_closed
    sleep 0.5
    sample :drum_stick  # Added stick sound after second closed cymbal
    sleep 0.25
  end
end




tune 4



in_thread do
  live_loop :drums do
    sample :drum_bass_soft
    sleep 0.25  # Reduced sleep time for faster rhythm
    sample :drum_stick  # Added stick sound after bass drum
    sleep 0.125  # Reduced sleep time for faster rhythm
    
    sample :drum_cymbal_closed
    sleep 0.25  # Reduced sleep time for faster rhythm
    sample :drum_stick  # Added stick sound after closed cymbal
    sleep 0.125  # Reduced sleep time for faster rhythm
    
    with_fx :reverb do
      sample :drum_snare_soft
      sleep 0.25  # Reduced sleep time for faster rhythm
      sample :drum_stick  # Added stick sound after snare
      sleep 0.125  # Reduced sleep time for faster rhythm
    end
    
    sample :drum_cymbal_closed
    sleep 0.25  # Reduced sleep time for faster rhythm
    sample :drum_stick  # Added stick sound after second closed cymbal
    sleep 0.125  # Reduced sleep time for faster rhythm
  end
end



tune 5



# Sonic Pi code for "Give Me Sunshine" with smooth and vibrant sound

use_bpm 120  # Set the tempo

# Define the melody notes and their durations
melody = [
  :e4, :g4, :a4, :b4, :a4, :g4, :e4, :d4,
  :e4, :g4, :a4, :b4, :a4, :g4, :e4, :d4,
  :c5, :b4, :a4, :g4, :f4, :e4, :d4, :e4,
  :g4, :a4, :b4, :a4, :g4, :e4, :d4, :e4,
  :e4, :g4, :a4, :b4, :a4, :g4, :e4, :d4,
  :e4, :g4, :a4, :b4, :a4, :g4, :e4, :d4,
  :c5, :b4, :a4, :g4, :f4, :e4, :d4, :e4,
  :g4, :a4, :b4, :a4, :g4, :e4, :d4
]

# Define the durations for each note
durations = [
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1,
  0.5, 0.5, 0.5, 0.5, 0.5, 0.5, 1, 1
]

# Play the melody with smooth and vibrant effects
live_loop :give_me_sunshine do
  melody.each_with_index do |note, index|
    # Use a soft synth for a smoother sound
    use_synth :saw
    play note, release: 0.8, amp: 0.7, attack: 0.2  # Increased attack for smoothness
    sleep durations[index]

    # Insert drums and bass every four melody notes
    if index % 4 == 0
      in_thread do
        # Drums loop
        sample :drum_bass_soft, amp: 0.8
        sleep 0.25
        sample :drum_stick, amp: 0.6
        sleep 0.05

        sample :drum_cymbal_closed, amp: 0.5
        sleep 0.25
        sample :drum_stick, amp: 0.6
        sleep 0.05

        with_fx :reverb do
          sample :drum_snare_soft, amp: 0.8
          sleep 0.25
          sample :drum_stick, amp: 0.6
          sleep 0.05
        end

        sample :drum_cymbal_closed, amp: 0.5
        sleep 0.25
        sample :drum_stick, amp: 0.6
        sleep 0.05
      end

      # Bass loop with smooth transitions
      in_thread do
        use_synth :fm
        play :c2, release: 0.4, amp: 0.6
        sleep 0.5
        play :e2, release: 0.4, amp: 0.6
        sleep 0.5
        play :g2, release: 0.4, amp: 0.6
        sleep 0.5
        play :b2, release: 0.4, amp: 0.6
        sleep 0.5
      end

      # Sticky sound loop
      in_thread do
        sync :give_me_sunshine  # Sync with melody for timing
        sample :drum_stick, amp: 0.8
        sleep 0.25  # Play sticky sound every quarter note
      end
    end
  end
end





