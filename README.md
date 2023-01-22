# Routing State with URL Parameters
### Step 1: Set up URL Property With Param(s)
```
.state('view1', {
    url: '/view1/{param1}',
    templateUrl: 'view1.html',
    controller: 'View1Ctrl as view1',
    resolve: {
        myData: ['$stateParams', function($stateParams){
            return getDataBasedOn($stateParams.param1);
        }]
    }
});
```
### Step 2: Inject Resolve Property Into Controller
```
View1Ctrl.$inject = ['myData'];
function View1Ctrl(myData){
    var view1 = this;
    view1.myData = myData;
}
```

```
<a ui-sref="view1({itemId:someVal})">
    Link to view with data
</a>
```
`view1` - state name

`{itemId:someVal}` - param name/value pairs