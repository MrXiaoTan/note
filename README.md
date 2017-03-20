### js的面像对象什么时候都可以用。平时写的时候如果你注重代码的可维护性和可读性也会用到。

打个比如说，在一个页面多个部分组成，其中有一部分按钮 触发的 是处理学生增删拆改，一部分按钮触发的是老师的增删拆改。 按一般写法看你是这样的。
```
var doAddStudent = function(){ ......}
var doDeleteStudent = function(){ ......}
var doAddTeacher = function(){...........}
var doDeleteTeacher= function(){ ......}
document.getElementById('addStudentBtn').addEventListener('onclick', doAddStudent)
document.getElementById('deleteStudentBtn').addEventListener('onclick', doDeleteStudent)
document.getElementById('addTeacherBtn').addEventListener('onclick', doAddTeacher)
document.getElementById('deleteTeacherBtn').addEventListener('onclick', doDeleteTeacher)
```
为每一个按钮绑定一个函数。这样固然是可以，但是换成面向对象处理后，可能更易读。

如
```
var StudentModule= {
    add: function(){....}
    delete: function(){...}
}
var TeachModule = {
    add: function(){...}
    delete: function(){...}
}
document.getElementById('addStudentBtn').addEventListener('onclick', StudentModule.add)
document.getElementById('deleteStudentBtn').addEventListener('onclick', StudentModule.delete)
document.getElementById('addTeacherBtn').addEventListener('onclick', TeachModule.add)
document.getElementById('deleteTeacherBtn').addEventListener('onclick', TeachModule.delete)
```

这里只是简单的举个例子。还如说看你的页面里面需要管理多个ajax请求，那么可以吧这些ajax请求的处理 页抽象处一个对象进行处理。总之面对对象可以想用就用，不想用页没关系。

对于那种页面结构很庞大时，不管是对于函数的处理，还是说全局对象（变量）的管理 抑或是 避免 全局变量污染 都有很大的帮助，对于代码的结构和可读性都有比较大的提升。