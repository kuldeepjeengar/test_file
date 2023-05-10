# test_file


pip install pydub
import os
import sys
from pydub import AudioSegment

def convert_to_wav(mp3_folder, output_folder):
   
    if not os.path.exists(output_folder):
        os.makedirs(output_folder)

    
    for filename in os.listdir(mp3_folder):
        if filename.endswith('.mp3'):
            mp3_path = os.path.join(mp3_folder, filename)
            wav_filename = os.path.splitext(filename)[0] + '.wav'
            wav_path = os.path.join(output_folder, wav_filename)

            
            audio = AudioSegment.from_mp3(mp3_path)

          
            audio.export(wav_path, format='wav')

            print(f'Converted: {filename} -> {wav_filename}')

if _name_ == '_main_':
    if len(sys.argv) < 3:
        print('Usage: python mp3_to_wav.py <mp3_folder> <output_folder>')
        sys.exit(1)

    mp3_folder = sys.argv[1]
    output_folder = sys.argv[2]

    convert_to_wav(mp3_folder, output_folder)
