
Parses a canvas Peer Review page and collates assignments that were submitted.

Each student will recieve a copy of their own assignment and the critique they wrote,
plus anonymous copies of the critiques written about their assignment.

1. download zip files from canvas to submissions.zip and critiques.zip,
   and then unzip them to submissions/ and critiques/ respectively

2. save the peer reviews page as peer_reviews.html

3. if there are any .docx submissions, convert them to pdf using pdflatex
   and pandoc (needs to be installed seperately)

       ls *.docx | \
         sed 's/.docx//;s/.*\///'| \
         xargs -L 1 -I % \
         pandoc -V fontsize=11pt -V linestretch=1.5 %.docx -o %.pdf

4. install "cpdf" or download it to the local directory and add it to your path.

    https://github.com/coherentgraphics/cpdf-binaries
    export PATH=.:$PATH

5. run `python collate.py peer_reviews.html`

[Licensed under the terms of the GPLv3](https://www.gnu.org/licenses/gpl-3.0.en.html)
