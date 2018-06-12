# DataGenerator


A simple simulator pushing a configurable amount of text to a socket. Originally implemented by Thor Martin Abrahamsen: https://github.com/thormartin91/twitter-stream

# Configuration

| Variable         | Description                                                       |	Values       |
| ---------------- | ----------------------------------------------------------------- | ------------- |
| TPS              |	Tweets pr. second                                                |	int          |
| REPEAT           |	Read the DATAFILE from the beginning when it reaches the end     |	true / false |
| CUTOFF           |	Stop stream after this number of Tweets                          |	int / null   |
| BUFFER_THRESHOLD |	Minimum factor of TPS to keep in buffer                          |	int          |
| DATAFILE         |	Source file to read text from. Each line is streamed as a Tweet  |	string       |
| PORT             |	Output port for the socket                                       |	int          |

Data is emitted to the socket on port <b>PORT</b> every second with the number <b>TPS</b> as a list of Tweets, collected from lines in the <b>DATAFILE</b>. The lines are loaded into a buffer, and the buffer size is always larger than <b>TPS</b> * <b>BUFFER_THRESHOLD</b>. If <b>REPEAT</b> is true, the server will continue until it reaches the <b>CUTOFF</b>, reading the <b>DATAFILE</b> again if it reaches the end. If <b>REPEAT</b> is false, and <b>CUTOFF</b> is null, the server will continue until it has read all lines in the <b>DATAFILE</b>.
