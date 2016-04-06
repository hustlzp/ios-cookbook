# UITableView

###自适应高度

`tableView.rowHeight`属性的默认值为`UITableViewAutomaticDimension`，代码中只需设置`estimatedRowHeight`即可实现基于AutoLayout的自适应高度：

```swift
tableView.estimatedRowHeight = 110
```

存在一个问题，如果cell的高度波动比较大，那么在`reloadData`的时候可能出现table的contentOffset跳变，解决方法是：

```swift
func tableView(tableView: UITableView, estimatedHeightForRowAtIndexPath indexPath: NSIndexPath) -> CGFloat {
    let question = questions[indexPath.row]

    return tableView.fd_heightForCellWithIdentifier(cellIdentifier, cacheByKey: question.objectId, configuration: { (cell) in
        (cell as! QuestionWithAnswerTableViewCell).update(question)
    })
}
```

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

###判断是否已注册cell class

```
if tableView.dequeueReusableCellWithIdentifier(cellIdentifier) == nil {
    tableView.registerClass(QuestionWithAnswerTableViewCell.self, forCellReuseIdentifier: cellIdentifier)
}
```