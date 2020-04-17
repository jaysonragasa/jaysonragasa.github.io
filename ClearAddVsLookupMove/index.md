![](https://raw.githubusercontent.com/jaysonragasa/jaraimages/master/ClearAddVsLookupMove/clearddvslookupmove.gif)

# Background
It's always been my practice but barely implemented that when just refreshing the list to show updated data or just sorting things. It's always better to move the items instead of clearing the list then showing the sorted items.  
  
I tried implementing this again here since our `ObservableCollection<T>` has 221 countries and we're not paging the lists. So comparing the lazy reloading (i.e. after sorting) and we use `.Clear()` and `.Add(T)` to refresh the items in the list against just moving the items `T LookupItem()` and `.Move(int index)`. The result is interesting.  

* Lazy loading took **450 to 500 +-** millisecond to complete EVERYTIME I sort the list
* Moving took only **60 to 90 +-** millisecond. That's a huge difference in performance. Codes may be a bit longer with this one plus the look up is using `.Where`. I think it may perform even more faster if I used the traditional loop.  
  
This duration will be different based on your device. But I'm already using Samsung Galaxy S8
