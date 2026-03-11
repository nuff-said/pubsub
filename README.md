# [@nuff-said/pubsub][repo-npm]

A compact pubsub implementation in **190 bytes** raw!

```javascript
import pubsub from '@nuff-said/pubsub'

pubsub.sub('event', () => {
	console.log('event fired!');
})

pubsub.sub('event', () => {
	console.log('event fired! this runs only once');
	return false; // stop listening
})

pubsub.pub('event'); // logs twice
pubsub.pub('event'); // logs once (second listener doesnt fire)

const eventID = pubsub.sub('otherthing', () => console.log('other thing'))
pubsub.pub('otherthing'); // logs
pubsub.unsub(eventID)
pubsub.pub('otherthing'); // nothing

pubsub.sub('data', (...data) => console.log(data));
pubsub.pub('data', 1, 'more', ['stuff']) // pass as much as you like
                                         // logs [1, 'more', ['stuff']]

pubsub.sub('test', console.log);
pubsub.sub('test', console.log);
pubsub.sub('test', console.log);
const read = pubsub.pub('test', 'hi')
read //=> ['test-5', 'test-6', 'test-7'] the ids of the listeners that were fired
```

## Installation

```shell
$ npm i @nuff-said/jsondb
```

## Contributing

All contributions are welcome! Feel free to file an issue, point out an
optimization or even push a PR!

## License

This project uses the GPL-3.0 license.

[repo-npm]: https://npm.im/@nuff-said/jsondb
