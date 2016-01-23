# CocoaPods

##查看可更新的pod

```
pod outdated
```

###pod install/pod update更新慢的问题

如果执行pod install还是pod update都卡在了Analyzing dependencies不动，原因在于每次执行以上两个命令的时候会升级CocoaPods的spec仓库，加一个参数`--no-repo-update`可以省略这一步，然后速度就会提升不少：

```
pod install  --no-repo-update
pod update --no-repo-update
```

###工程文件损坏的处理方法

删除`*.workspace`、`Podfile.lock`、`Pods`，然后运行`pod install`，再用Xcode打开workspace文件。