<style>
    * {
        margin:0;
        padding:0;
    }
    .overlay {
        width: 100px;
        height: 300px;
        background: green;
    }
    input,select {
        display:block;
        margin:10px;
    }
</style>

<input type="button" id="trigger1" value="基本对话框" />
<select>
    <option value="1">one</option>
</select>
<input type="button" id="trigger2" value="淡入淡出对话框" />
<input type="button" id="trigger3" value="水平展开对话框" />
<input type="button" id="trigger4" value="垂直展开对话框" />
<input type="button" id="trigger5" value="从左移入对话框" />
<input type="button" id="trigger6" value="从右移入对话框" />
<input type="button" id="trigger7" value="从上移入对话框" />
<input type="button" id="trigger8" value="从下移入对话框" />
<input type="button" id="trigger8-1" value="混合动画对话框一" />
<input type="button" id="trigger8-2" value="混合动画对话框二" />

<input type="button" id="trigger9" value="ajax对话框" />
<input type="button" id="trigger10" value="iframe对话框" />
    
```javascript
seajs.use(['baseDialog', 'animDialog'], function(BaseDialog, AnimDialog) {
    
    var closeDialogTpl = '<div class="overlay"><button id="close">点击关闭</button><p>肯定是房间里萨的看法金克拉束带结发<a style="color:#fff;font-size:14px;padding-top:10px;" href="javascript:void(0)" data-overlay-role="trigger" data-overlay-action="hide">点击这里也可以关闭</a></p></div>';
    var dialogTpl = '<div class="overlay"><div id="dialog-title"></div><div id="dialog-content"></div><button id="confirm">确认按钮</button><button id="close">点击关闭</button></div>';

    var d1 = new BaseDialog({
        trigger: '#trigger1',
        template: dialogTpl,
        width: 100,
        height: 200,
        confirmElement: '#confirm',
        closeElement: '#close',
        titleElement: '#dialog-title',
        title: '我是标题',
        contentElement: '#dialog-content',
        content: '我是内容',
        onConfirm: function() {
            alert('点击了确定按钮');
        },
        onClose: function() {
            alert('点击了关闭按钮');
        },
        align: {
            baseXY: [200, 200]
        },
        hasMask: true
    });
    d1.set('content', '改变的内容');
    d1.set('width', 150);

    var d2 = new AnimDialog({
        trigger: '#trigger2',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 20]
        },
        effect: {
            type: 'fade'
        }
    });
    var d3 = new AnimDialog({
        trigger: '#trigger3',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 30]
        },
        effect: {
            type: 'slide',
            from: 'left'
        }
    });
    var d4 = new AnimDialog({
        trigger: '#trigger4',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 200]
        },
        effect: {
            type: 'slide',
            from: 'up'
        }
    });
    var d5 = new AnimDialog({
        trigger: '#trigger5',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 30]
        },
        effect: {
            type: 'move',
            from: 'left'
        }
    });
    var d6 = new AnimDialog({
        trigger: '#trigger6',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 40]
        },
        effect: {
            type: 'move',
            from: 'right'
        }
    });
    var d7 = new AnimDialog({
        trigger: '#trigger7',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [20, 60]
        },
        effect: {
            type: 'move',
            from: 'up'
        }
    });
    var d8 = new AnimDialog({
        trigger: '#trigger8',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 200]
        },
        effect: {
            type: 'move',
            from: 'down'
        }
    });
    var d8_1 = new AnimDialog({
        trigger: '#trigger8-1',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 200]
        },
        showEffect: {
            type: 'move',
            from: 'down'
        },
        hideEffect: {
            type: 'fade'
        }
    });
    var d8_2 = new AnimDialog({
        trigger: '#trigger8-2',
        template: closeDialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        align: {
            baseXY: [10, 200]
        },
        showEffect: {
            type: 'none'
        },
        hideEffect: {
            type: 'move',
            from: 'left'
        }
    });

    var d9 = new BaseDialog({
        trigger: '#trigger9',
        template: dialogTpl,
        width: 100,
        height: 200,
        closeElement: '#close',
        titleElement: '#dialog-title',
        title: function() {
            return '我真是标题';
        },
        contentElement: '#dialog-content',
        ajaxUrl: 'https://www.alipay.com/',        
        align: {
            baseXY: [10, 200]
        }
    });
    var d10 = new BaseDialog({
        trigger: '#trigger10',
        template: '<div class="overlay"><div id="dialog-title"></div><iframe src=""></iframe><button id="close">点击关闭</button></div>',
        width: 'auto',
        height: 200,
        closeElement: '#close',
        titleElement: '#dialog-title',
        title: function() {
            return '我真是标题啊';
        },
        align: {
            baseXY: [10, 200]
        },
        iframeUrl: 'https://www.alipay.com/'
    });
});
```


