## 1.1流程控制

## 1.2全局作用域/局部作用域/作用域链
    1.全局作用域
    2.局部作用域
    3.作用域链
## 1.3冒泡排序

## 1.4闭包
> 闭包（closure）指有权访问另一个函数作用域的函数  ----- Javascript高级程序设计

作用：延伸变量作用范围

## 1.5递归
> 如果一个函数在内部可以调用函数本身，那么这个函数就是递归函数

简单来说：函数内部自己调用自己，那么这个函数就是递归函数

#### 1.5.1利用递归从树中获取匹配对象

根据组织id获取对应组织对象

````
    let orgTree=[
        {
            id:'test',
            name:'众康云医院',
            children:[
                {
                    id:'test2',
                    name:'心血管科室',
                }
            ]
        },
        {
            id:'dadad',
            name:'江北医院'
        }
    ];

    function getCurrentItem(id,tree,index=0){
        let item = tree[index];
        if(item.id==id){
            return item
        }else{
            if(item.children&&item.children.length){
                let find = getCurrentItem(id,item.children);
                if(find&&find.id==id){
                    return find
                }
            }
            return getCurrentItem(id,tree,++index)
        }
    }

    getCurrentItem('test2',orgTree)
````

#### 1.5.2利用递归实现深拷贝
````
function deepCopy(oldObj){
    let newObj=null;
    for(let key in oldObj){
        let item=oldObj[key];
        //1.判断是否数组
        //2.判断是否对象
        //3.是否简单数据
        if(Array.isArray(item)){
            newObj=newObj||[];
            newObj[key]=deepCopy(item,[]);
        }else if(item instanceof Object){
            newObj=newObj||{};
            newObj[key]=deepCopy(item,{});
        }else{
            newObj=newObj||{};
            newObj[key] = item;
        }
    }
    return newObj
}
````