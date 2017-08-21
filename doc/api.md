
注意，Promise()不允许在外部被初始化。通过实例化`Promise.Defer()`来使用Promise的功能。Promise 实例方法有：

### then()  `<Promise 实例方法>`

`then ( fulfilled [, rejected] ) => void`

监听当前实例的成功和失败并返回新的 promise 实例

#### parameter

- fulfilled (Function) – 该 promise 成功时的回调，参数为 defer resolve 时的 value.
- rejected (Function) – 该 promise 失败时的回调，参数为 defer reject 时的 reason.

#### return

一个新的 promise（Promise类型）. 当前 promise 成功时新的 promise 也成功. 当前 promise 失败时新的 promise 也失败.

#### example

参照首[Demo](/5.0/demos/promise/index.html)。 这里为链式调用写法。

	require(['node', 'promise'],function(Node,Promise){
		Node.all("button").on("click", function () {
			// 生成一个Promise实例d
			var d = new Promise.Defer();
			var promise = d.promise;
			promise.then(function (v) {
				return v + 1;
			}).then(function (v) {
				alert(v); // => 2
			});
			d.resolve(1); // 该位置也可以放在 then 前面
		});
	});

### fail()  `<Promise 实例方法>`

` fail ( rejected ) => void`

监听当前实例的失败并返回新的 promise 实例.相当于调用 `this.then(null,rejected)`;

#### parameter

rejected (Function) – 该 promise 失败时的回调，参数为 defer reject 时的 reason.

#### return

一个新的 promise(（Promise类型）. 当前 promise 成功时新的 promise 也成功. 当前 promise 失败时新的 promise 也失败.

### fin()  `<Promise 实例方法>`

`fin ( callback ) => void`

监听当前实例的成功和失败并返回新的 promise 实例

#### parameter

callback (Function) – 该 promise 成功或失败时的回调， 成功时参数为 defer resolve 时的 value 和 true. 失败时参数为 defer reject 时的 reason 和 false.

#### return

一个新的 promise. 当前 promise 成功时新的 promise 也成功. 当前 promise 失败时新的 promise 也失败.

### isResolved()  `<Promise 实例方法>`

`isResolved () => Boolean`

返回当前 promise 是否成功了

### isResolved() `<static>`

`isResolved () => Boolean`

静态方法，作用同上

	Promise.isResolved(promise)

### isRejected()  `<Promise 实例方法>`

`isRejected () => Boolean`

返回当前 promise 是否失败了

### isRejected() `<static>`

`isRejected () => Boolean`

静态方法，作用同上

	Promise.isRejected(promise)

### isPromise() `<static>`

`isPromise() => Boolean`

静态方法，判断一个对象是否是Promise实例

	Promise.isPromise(promise)

### when() `<static>`

`when(obj, fulfilled, rejected) => Promise`

返回一个新的 promise。如果 obj 为 promise 类型，相当于 `obj.then(fulfilled, rejected)`

否则直接调用 `fulfilled(obj)`，并返回一个成功的 promise

#### parameter

obj – 监听的对象.

### all() `<static>`

`all(objects) => Promise`

返回一个新的 promise.当 objects 全部成功后新的 promise 成功，否以第一个 promise 的失败值为失败

#### parameter

objects – promise或普通对象数组