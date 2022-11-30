- 👋 Hi, I’m @Comet676
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
Comet676/Comet676 is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
$ make base.en

cc  -I.              -O3 -std=c11   -pthread -DGGML_USE_ACCELERATE   -c ggml.c -o ggml.o
c++ -I. -I./examples -O3 -std=c++11 -pthread -c whisper.cpp -o whisper.o
c++ -I. -I./examples -O3 -std=c++11 -pthread examples/main/main.cpp whisper.o ggml.o -o main  -framework Accelerate
./main -h

usage: ./main [options] file0.wav file1.wav ...

options:
  -h,       --help          [default] show this help message and exit
  -t N,     --threads N     [4      ] number of threads to use during computation
  -p N,     --processors N  [1      ] number of processors to use during computation
  -ot N,    --offset-t N    [0      ] time offset in milliseconds
  -on N,    --offset-n N    [0      ] segment index offset
  -d  N,    --duration N    [0      ] duration of audio to process in milliseconds
  -mc N,    --max-context N [-1     ] maximum number of text context tokens to store
  -ml N,    --max-len N     [0      ] maximum segment length in characters
  -wt N,    --word-thold N  [0.01   ] word timestamp probability threshold
  -su,      --speed-up      [false  ] speed up audio by x2 (reduced accuracy)
  -tr,      --translate     [false  ] translate from source language to english
  -otxt,    --output-txt    [false  ] output result in a text file
  -ovtt,    --output-vtt    [false  ] output result in a vtt file
  -osrt,    --output-srt    [false  ] output result in a srt file
  -owts,    --output-words  [false  ] output script for generating karaoke video
  -ps,      --print-special [false  ] print special tokens
  -pc,      --print-colors  [false  ] print colors
  -nt,      --no-timestamps [true   ] do not print timestamps
  -l LANG,  --language LANG [en     ] spoken language
  -m FNAME, --model FNAME   [models/ggml-base.en.bin] model path
  -f FNAME, --file FNAME    [       ] input WAV file path

bash ./models/download-ggml-model.sh base.en
Downloading ggml model base.en ...
ggml-base.en.bin               100%[========================>] 141.11M  6.34MB/s    in 24
