# AttributedString

###UILable与NSParagraphStyle冲突的地方

* textAlignment
* lineBreakMode

如果使用了NSParagraphStyle，那么直接对UILabel设置以上属性无效，而应该对NSParagraphStyle设置。