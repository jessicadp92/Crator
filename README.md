# 🕷️ Dark Web Crawler

A Python-based crawler designed to analyze **Tor hidden services (.onion)** starting from a single seed URL.  
The crawler supports configurable depth, timing, and proxy settings and is intended for **research and analysis purposes**.

> ⚠️ **Disclaimer**  
> This project is for educational and research use only.  
> Crawling the dark web may be illegal or restricted in some jurisdictions.  
> You are responsible for complying with all applicable laws.

---

## ✨ Features

- Crawl `.onion` websites via **Tor (SOCKS5)**
- Configurable crawl depth and execution limits
- Randomized delays between HTTP requests
- Project-based output directories
- Single-seed execution model

---

## 📁 Project Structure


---

## ⚙️ Configuration

### 1️⃣ Seed URL (`seeds.txt`)

`seeds.txt` contains the starting URL to analyze.
example: http://examplehiddenservice.onion

> ℹ️ **Note**  
> The crawler currently supports **one seed per execution**.

---

### 2️⃣ Crawler Configuration (`crator.yml`)

Example configuration:

```yaml

crawler.depth: 2
crawler.max_links: 1000000
crawler.max_time: 86400
crawler.random_wait: true
crawler.wait_request: 1500

data_directory: /home/your_user/path_to_data
http_proxy: socks5h://localhost:9050
project_name: your_project_folder_name
```

---

#### Parameters

| Parameter | Description |
|----------|-------------|
| `crawler.depth` | Maximum crawl depth |
| `crawler.max_links` | Maximum number of links to analyze |
| `crawler.max_time` | Maximum execution time (seconds) |
| `crawler.random_wait` | If `true`, the delay between requests is randomized by ±1 second |
| `crawler.wait_request` | Base delay between requests (milliseconds) |
| `data_directory` | Directory where crawl data will be stored |
| `http_proxy` | SOCKS5 proxy used to route traffic through Tor |
| `project_name` | Name of the output project folder |

---

## 🔐 Requirements

### 3️⃣ VPN and Tor

Before execution:

- Install and enable a **VPN**
- Install and run **Tor** locally

Tor installation guide:  
👉 https://ubuntuhandbook.org/index.php/2021/01/install-tor-tor-browser-ubuntu-20-10-20-04/

---

### 4️⃣ Verify Tor Is Running

Check that Tor is listening on port `9050`:

```bash
netstat -tulnp | grep 9050
```

Or test Tor connectivity:

```bash
curl --socks5-hostname localhost:9050 https://check.torproject.org
```

---

### 5️⃣ Install Python

Ensure Python 3 is installed on your system:

```bash
python3 --version
```

Recommended version: Python 3.8 or higher

If Python is not installed, download it from the official website:
👉 https://www.python.org/downloads/

---

### 6️⃣ Install Dependencies

Install all required Python packages using pip:

```bash
pip install -r requirements.txt
```

Using a virtual environment is recommended.
---

## ▶️ Usage

### Run the Crawler

From the python folder directory, execute:

```bash
python3 crator.py
```

During execution, the crawler will:

- Read the seed URL from seeds.txt
- Load configuration settings from crator.yml
- Route all network traffic through the Tor SOCKS5 proxy
- Crawl links according to the configured depth and limits
- Store collected data inside the configured data_directory

## 📝 Notes

- Running the crawler without **Tor** and a **VPN** is strongly discouraged
- Crawling Tor hidden services may be slow and unstable
- Large values for crawl depth, link limits, or execution time may consume significant system resources
- Some `.onion` services may be unavailable or intentionally misleading
- Use this tool responsibly and for research purposes only
