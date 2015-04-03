## Fixes for GoogleMapsWidget for ipython 2.2.0 -> 3.0.0

### Under ```In [2]:```

Fix 1: call super.__init__() within GoogleMapsWidget 

```
  def __init__(self, lng=0.0, lat=0.0, zoom=2):
+      super(GoogleMapsWidget,self).__init__()
```

### Under ```In [4]:```

Fix 2: require widget and manager separately 

```
- require(["widgets/js/widget"], function(WidgetManager){
+ require(["widgets/js/widget","widgets/js/manager"], function(widget, manager){
```

Fix 3: DOMWidgetView is now a member of widget, IPython object no longer exists

```
-     var GoogleMapsView = IPython.DOMWidgetView.extend({
+     var GoogleMapsView = widget.DOMWidgetView.extend({
```

Fix 4: WidgetManager is now a member of manager

```
-     WidgetManager.register_widget_view('GoogleMapsView', GoogleMapsView);
+     manager.WidgetManager.register_widget_view('GoogleMapsView', GoogleMapsView);
```
