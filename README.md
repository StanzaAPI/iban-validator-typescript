# Global IBAN, BIC/SWIFT & Bank Routing Validator API — TypeScript / JavaScript SDK

[![npm version](https://img.shields.io/npm/v/@stanzaapi/iban-validator.svg)](https://www.npmjs.com/package/@stanzaapi/iban-validator)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Stanza API](https://img.shields.io/badge/Powered%20by-Stanza-blue)](https://stanzaapi.com)

> ISO 13616 MOD-97 IBAN checksum verification, ISO 9362 BIC/SWIFT validation, and national bank routing extraction across 87 countries.

Official, zero-dependency Node.js and TypeScript client for **Global IBAN, BIC/SWIFT & Bank Routing Validator API**, powered by the [Stanza Micro-API Network](https://stanzaapi.com). Delivers deterministic, sub-5ms V8 isolate execution directly to your application without 3rd-party proxies.

* 🌐 **Live Web Sandbox:** [Try interactive queries online](https://stanzaapi.com/tools/iban-validator)
* 📚 **API Reference:** [Read complete OpenAPI specification](https://stanzaapi.com/tools/iban-validator)
* ⚡ **Platform Overview:** [Discover the Stanza Edge Portfolio](https://stanzaapi.com)

---

## 📦 Installation

```bash
npm install @stanzaapi/iban-validator
# or
pnpm add @stanzaapi/iban-validator
# or
yarn add @stanzaapi/iban-validator
```

---

## 🚀 Quickstart

```typescript
import { IbanValidatorClient } from '@stanzaapi/iban-validator';

// Initialize client (API key optional for sandbox tier evaluation)
const client = new IbanValidatorClient({
  apiKey: process.env.STANZA_API_KEY,
});

async function main() {
  const result = await client.validate('DE89370400440532013000');

  if (result.success) {
    console.log('Verification Success:', result.data);
  } else {
    console.error('Validation Error:', result.error, result.code);
  }
}

main().catch(console.error);
```

---

## 📄 Example JSON Response

```json
{
  "success": true,
  "data": {
    "valid": true,
    "iban": "DE89370400440532013000",
    "country_code": "DE",
    "bank_code": "37040044",
    "bic_candidate": "COBADEFFXXX"
  }
}
```

---

## ⚙️ Client Configuration Options

| Option | Type | Default | Description |
| :--- | :--- | :--- | :--- |
| `apiKey` | `string` | `process.env.STANZA_API_KEY` | Your [Stanza API Key](https://stanzaapi.com). Required for high-throughput production tiers. |
| `baseUrl` | `string` | `https://api.stanzaapi.com/iban-validator` | Public edge API base URL. |
| `timeoutMs` | `number` | `15000` | Request timeout in milliseconds (uses native `AbortSignal.timeout`). |


---

## 🛡️ Response Envelope & Error Handling

All responses return a typed envelope:

```typescript
export interface ApiResponse<T> {
  success: boolean;
  data?: T;
  error?: string;
  code?: 'VALIDATION_ERROR' | 'UNAUTHORIZED' | 'PAYLOAD_TOO_LARGE' | 'RATE_LIMITED' | 'INTERNAL_ERROR';
}
```

---

## 🔗 Related Resources

* [Global IBAN, BIC/SWIFT & Bank Routing Validator API Interactive Playground](https://stanzaapi.com/tools/iban-validator)
* [Stanza Microservices Directory](https://stanzaapi.com)
* [Report an Issue on GitHub](https://github.com/StanzaAPI/iban-validator-typescript/issues)

## 📄 License

MIT © Stanza — Powered by [Stanza](https://stanzaapi.com).
