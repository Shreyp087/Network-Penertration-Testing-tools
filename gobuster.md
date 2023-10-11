# Detailed Documentation on Using GoBuster for Network Penetration Testing

GoBuster is an open-source tool designed for directory and file brute-forcing. It is a popular choice for network penetration testers to discover hidden files and directories on web servers. This documentation will guide you through using GoBuster effectively for network penetration testing.

## Installation

GoBuster is written in Go, so you need to have Go installed on your system. You can install GoBuster using the `go get` command:

```bash
go get github.com/OJ/gobuster/v3
```

After successful installation, GoBuster will be available as a command-line tool.

## Basic Usage

### 1. Basic Directory Brute Force

To perform a basic directory brute force using GoBuster, you need to specify the target URL and the wordlist you want to use. The following command will search for common directories on a target web server:

```bash
gobuster dir -u <target_url> -w <wordlist>
```

- Replace `<target_url>` with the URL of the web server you want to scan.
- Replace `<wordlist>` with the path to the wordlist file that contains potential directory or file names.

### 2. Default Wordlists

GoBuster includes several default wordlists for common directory and file names. You can use these built-in wordlists with the `-w` option. For example:

```bash
gobuster dir -u <target_url> -w common.txt
```

This command uses the `common.txt` wordlist provided by GoBuster.

### 3. Displaying Progress

GoBuster will display its progress and results as it scans. You can use the `-t` option to set the number of concurrent threads for faster scanning. For example:

```bash
gobuster dir -u <target_url> -w <wordlist> -t 10
```

This command uses 10 threads for concurrent scanning.

### 4. Output to a File

You can save the scan results to a file using the `-o` option:

```bash
gobuster dir -u <target_url> -w <wordlist> -o results.txt
```

This will save the results to a file named `results.txt` in the current directory.

## Advanced Usage

### 1. Extending Wordlists

GoBuster allows you to use custom wordlists for more targeted scans. You can create your wordlists or combine multiple wordlists to perform comprehensive scans.

```bash
gobuster dir -u <target_url> -w custom_wordlist.txt
```

### 2. Status Codes

You can filter results based on HTTP status codes using the `-s` option. For example, to only display results with status code 200 and 204:

```bash
gobuster dir -u <target_url> -w <wordlist> -s "200,204"
```

### 3. Filtering Extensions

GoBuster can filter results based on file extensions using the `-x` option. For example, to search for directories and .php files:

```bash
gobuster dir -u <target_url> -w <wordlist> -x "php,/"
```

### 4. Custom User-Agent

You can set a custom User-Agent header using the `-a` option. For example:

```bash
gobuster dir -u <target_url> -w <wordlist> -a "Mozilla/5.0 (Windows NT 10.0; Win64)"
```

### 5. Cookies

If the web server requires a specific cookie for access, you can set it using the `-c` option:

```bash
gobuster dir -u <target_url> -w <wordlist> -c "session=12345"
```

### 6. HTTP Authentication

If the web server is protected by HTTP Basic Authentication, you can provide credentials using the `-U` and `-P` options:

```bash
gobuster dir -u <target_url> -w <wordlist> -U username -P password
```

### 7. Recursive Scanning

GoBuster can perform recursive scanning by using the `-r` option:

```bash
gobuster dir -u <target_url> -w <wordlist> -r
```

This will search for directories and files recursively.

## Conclusion

GoBuster is a versatile tool for directory and file brute-forcing in network penetration testing. This documentation provides an overview of its capabilities, from basic scans to advanced customization options. Always use GoBuster responsibly and ensure that you have explicit authorization to conduct network penetration tests, as unauthorized testing is illegal and unethical.
