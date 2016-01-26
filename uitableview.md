# UITableView

###自适应高度



###调节seperator样式

* separatorColor
* separatorInset

###在Cell之间添加间隔

**Section法**：


```swift
// 一定要设置style为Grouped，否则section会置顶
let tableView = UITableView(frame: CGRect.zero, style: .Grouped)

func numberOfSectionsInTableView(tableView: UITableView) -> Int {
    return recommendations.count
}
    
func tableView(tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return 1
}

func tableView(tableView: UITableView, heightForFooterInSection section: Int) -> CGFloat {
    return CGFloat.min;
}

func tableView(tableView: UITableView, heightForHeaderInSection section: Int) -> CGFloat {
    if section == 0 {
        return CGFloat.min
    } else {
        return 10
    }
}

func tableView(tableView: UITableView, viewForHeaderInSection section: Int) -> UIView? {
    let headerView = UIView()
    headerView.backgroundColor = UIColor.whiteColor()
    return headerView
}
```

[出处](http://stackoverflow.com/a/21901250/1954737)