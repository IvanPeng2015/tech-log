## 单向数据流／副作用

应该忌讳在componentDidUpdate或者componentWillReceiveProps上检测数据改变了然后触发action或者执行setState。
这种形式是Observable数据流程，应该去使用rxjs或者用redux-observable，会很混乱，找不到action和setState因为啥触发的
不是redux的控制副作用的单向数据流。

很多同学仅仅用了一个双向绑定。然后，事件自己来，数据传输自己来，状态变化自己来。利用库的API监控数据变化，进而进行数据切换。

我们之所以，从数据监控API watch中转移出来，之所以从全局diff检测算法componentDidUpdate中跳出来，从脏检查依赖抽离出来......为的是将状态管理从组件这个单元系统中独立出来，独立出来的系统可以使用很多种方案或者思路进行管理
