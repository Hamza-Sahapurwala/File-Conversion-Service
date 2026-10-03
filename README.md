# Distributed File Conversion Service

A client-server system that converts DOCX files to PDF over a network. Clients upload a file over TCP, the server queues the job, and a pool of worker threads converts it and returns the result.

## Authors

- Chiranthan Shankar (PES2UG24CS137)

- Hamza Shabbir Sahapurwala (PES2UG24CS177)

## How It Works

1. The client connects to the server and uploads a `.docx` file.
2. The server adds the job to a queue.
3. One of three worker threads picks up the job and converts the file.
4. The server sends the converted PDF back to the client.

The server handles multiple clients at once, and the queue ensures jobs are processed in order.

## Project Structure

| File | Purpose |
| --- | --- |
| `server.py` | TCP server, job queue and worker threads |
| `conversion.py` | DOCX to PDF conversion |
| `client.py` | Command-line client for uploading files |
| `performancegraph.py` | Plots results from `performance.csv` |
| `Testfiles/` | Sample files for testing |
| `Documents/`| Contains Project Report |

## Requirements

- Python 3.8+
- `python-docx`
- `reportlab`

```
pip install python-docx reportlab
```

## Usage

Start the server (listens on port 5001):

```
python server.py
```

Set the server's IP address in `client.py`, then run the client:

```
python client.py
```

Enter the path to a `.docx` file when prompted. The converted PDF is returned to the client.

The client and server must be on the same network.

## Limitations

- Only `.docx` to `.pdf` conversion is implemented.
- Conversion extracts paragraph text only. Images, tables and complex formatting are not preserved.
