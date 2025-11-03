<p align="center">
    <img src="https://raw.githubusercontent.com/SiMotionBG/use-ua-parser-next/master/misc/logo.png" width="512" height="256"> 
</p>

<p align="center">
<a href="https://travis-ci.org/faisalman/ua-parser-js"><img src="https://travis-ci.org/faisalman/ua-parser-js.svg?branch=master"></a>
<a href="https://www.npmjs.com/package/use-ua-parser-next"><img src="https://img.shields.io/npm/v/use-ua-parser-next.svg"></a>
</p>

# useUA React Hook

Fork of use-ua-parser-react which adds compatiblity for NextJS (and React Server Components), built on top of UAParser.js library to detect Browser, Engine, OS, CPU, and Device type/model from User-Agent data

- NextJS-compatiblle version author: SiMotin BG https://simotionbg.com
- Hook author: Kemal Erdem https://erdem.pl
- UAParse.js author : Faisal Salman <<f@faisalman.com>>
- Demo : https://faisalman.github.io/ua-parser-js
- Source : https://github.com/burnpiro/use-ua-parser-next

# Installation

```bash
npm i use-ua-parser-next
```

```bash
yarn add use-ua-parser-next
```

# Usage

```javascript
"use client" // Can't use hooks in server components
import { useUA } from 'use-ua-parser-next';

const MyComponent: FC<Props> = (props) => {
  const UADetails = useUA(); // Get current browser data
  [...]
}
```

Return:

```typescript
{
  ua: string,
  browser: { name: string, version: string },
  cpu: { architecture: string },
  device: { model: string, type: string, vendor: string },
  engine: { name: string, version: string },
  os: { name: string, version: string }
}
```

### Options

Parse custom userAgent:

```javascript
"use client"
import { useUA } from 'use-ua-parser-next';

const customAgent = 'Mozilla/5.0 (iPhone; U; CPU iPhone OS 5_1_1 like Mac OS X; en) AppleWebKit/534.46.0 (KHTML, like Gecko) CriOS/19.0.1084.60 Mobile/9B206 Safari/7534.48.3';
const MyComponent: FC<Props> = (props) => {
  const UADetails = useUA(customAgent);
  [...]
}
```

# Other Hooks

### `useDevice(uaString?: string)`:

```javascript
'use client';
import { useDevice } from 'use-ua-parser-next';

const MyComponent: FC<Props> = (props) => {
  const device = useDevice(); //{ model: string, type: string, vendor: string }
};
```

### `useBrowser(uaString?: string)`:

```javascript
'use client';
import { useBrowser } from 'use-ua-parser-next';

const MyComponent: FC<Props> = (props) => {
  const browser = useBrowser(); //{ name: string, version: string }
};
```

### `useCPU(uaString?: string)`:

```javascript
'use client';
import { useCPU } from 'use-ua-parser-next';

const MyComponent: FC<Props> = (props) => {
  const cpu = useCPU(); //{ architecture: string }
};
```

### `useEngine(uaString?: string)`:

```javascript
'use client';
import { useEngine } from 'use-ua-parser-next';

const myComponent: FC<Props> = (props) => {
  const engine = useEngine(); //{ name: string, version: string }
};
```

## Helpers

### `isMobile(device: UAParser.IResult['device']): boolean`

```javascript
'use client';
import { useDevice, isMobile } from 'use-ua-parser-next';

const myComponent: FC<Props> = (props) => {
  const device = useDevice(); //{ model: string, type: string, vendor: string }
  const isCurrentDeviceMobile = isMobile(device);
};
```

### `isTouchDevice(device: UAParser.IResult['device']): boolean`

Check if device is either a `mobile`, `tablet` or `wearable` device. Doesn't include "2:1" laptops.

```javascript
'use client';
import { useDevice, isTouchDevice } from 'use-ua-parser-next';

const myComponent: FC<Props> = (props) => {
  const device = useDevice(); //{ model: string, type: string, vendor: string }
  const hasTouchScreen = isTouchDevice(device);
};
```
