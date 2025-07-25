# curl-cffi

A powerful HTTP client for Node.js based on libcurl with browser fingerprinting capabilities.

[English](https://github.com/tocha688/curl-cffi-node/blob/main/README.md) | [中文](https://github.com/tocha688/curl-cffi-node/blob/main/README.zh.md)

<a name="english"></a>

## Introduction

curl-cffi is a high-performance HTTP client library for Node.js built on libcurl. It provides both synchronous and asynchronous request methods with powerful browser fingerprinting capabilities, making it ideal for web scraping, API testing, and automation tasks that require browser simulation.

### Key Features

- **Multiple Request Modes**: Support for both synchronous and asynchronous requests
- **Browser Fingerprinting**: Simulate various browsers including Chrome, Firefox, Safari, Edge, and Tor
- **Session Management**: Maintain cookies and configurations across requests
- **Rich Configuration Options**: Comprehensive control over HTTP requests
- **JA3/TLS Fingerprinting**: Advanced TLS fingerprint simulation

### Use Cases

- Web scraping with browser simulation
- API testing and integration
- Automated web interactions
- Network request debugging
- Bypassing basic anti-bot measures

## Installation

```bash
npm install curl-cffi
```

## Basic Usage

### Simple Request

```javascript
const { req } = require('curl-cffi');

// Asynchronous request
async function makeGetRequest() {
  try {
    const response = await req.get('https://api.example.com/data', {
      impersonate: 'chrome136' // Simulate Chrome 136
    });
    console.log('Status Code:', response.statusCode);
    console.log('Response Data:', response.data);
  } catch (error) {
    console.error('Request failed:', error);
  }
}

makeGetRequest();
```

### Synchronous and Asynchronous Requests

curl-cffi supports both synchronous and asynchronous request modes:

```javascript
// Synchronous request
const { CurlRequestSync } = require('curl-cffi');
const syncCurl = new CurlRequestSync();

// Asynchronous request with event-based implementation
const { CurlRequest } = require('curl-cffi');
const asyncCurl = new CurlRequest();

// Asynchronous request with timer-based implementation
const { CurlRequestLoop } = require('curl-cffi');
const loopCurl = new CurlRequestLoop();
```

### Session Management

```javascript
const { CurlSession, CurlSessionSync, CurlSessionLoop } = require('curl-cffi');

// Session Request
const req1 = new CurlSession()
// Synchronous session implementation
const req2 = new CurlSessionSync()
// Timer-based session implementation
const req3 = new CurlSessionLoop()
```

### Performance Optimization

```javascript
// Use global interface to reuse connections and improve performance
const req1 = new CurlSession({impl: gimpl})
```

## License

This project is licensed under the MIT License - see the LICENSE file for details.

**Inspired by** [curl_cffi](https://github.com/lexiforest/curl_cffi)  
**libcurl** [curl-impersonate](https://github.com/lexiforest/curl-impersonate)
