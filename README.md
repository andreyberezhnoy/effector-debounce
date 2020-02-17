# Effector Debounce

https://codesandbox.io/s/effector-throttle-debounce-w32tk

## Installation

```bash
npm install --save effector effector-debounce

# or

yarn add effector effector-debounce
```

## Usage

Create event that should be debounced:

```ts
import { createEvent } from 'effector';

const someHappened = createEvent<number>();
```

Create debounced event from it:

```ts
import { createDebounce } from 'effector-debounce';

const DEBOUNCE_TIMEOUT_IN_MS = 200;

const debounced = createDebounce(someHappened, DEBOUNCE_TIMEOUT_IN_MS);
```

To test that original event is correctly debounced you can add watcher:

```ts
someHappened.watch((payload) => {
  console.info('someHappened now', payload);
});

debounced(1);
debounced(2);
debounced(3);
debounced(4);
```