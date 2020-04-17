![](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/ClearAddVsLookupMove/clearddvslookupmove.gif)

# Background
It's always in my thought but barely implemented that when just refreshing the list to show updated data or just sorting things. It's always better to move the items around instead of clearing the list then showing the sorted items. I implemented this before, way back 2015 when I was working on a Kiosk WPF app and in administration mode there are lists that shows real time updates.. and it's pain watching the list clearing and then repopulating when something changes in the background. It's ugly, it's slow, and you can't click on it.  
  
I am working on a simple project called [COVID19 Tracker](https://github.com/jaysonragasa/COVID19Tracker) were I need to sort different columns of COVID19 cases -- Country, Confirmed Case, Total Recoveries, Total Deaths. When I click on the column headers, I noticed this very slow performance when **repopulating** the ListView and it even got slower when the hot reload triggers the refresh of the entire page.  
  
Look at the duration here  
![](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/ClearAddVsLookupMove/clearddvslookupmove_gotworst.gif)
  
The ListView is bound on an `ObservableCollection<T>` and has 221 items in it. We're not paging for the mean time. I also have a `List<T>` where I keep a backup for sorting purposes. So comparing the result of usinig lazy reloading were we use `.Clear()` and `.Add(T)` to refresh the items in the list against just moving the items `T LookupItem()` and `.Move(int index)`. The result is interesting.  
  
* Lazy loading took **100 to 130 +-** millisecond to complete EVERYTIME I sort the list
* Moving took only **20 to 30 +-** millisecond. That's a huge difference in performance. Codes may be a bit longer with this one plus the look up is using `.Where`. I think it may perform even more faster if I used the traditional loop.  
  
This duration will be different of course based on your device. In my device, the lazy load took 300+- ms and using Move took only around 60+-ms.
