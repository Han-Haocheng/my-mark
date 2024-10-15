---
tags:
  - level_0
---


# 目录

- [00-设计模式](0204-设计模式/00-设计模式.md)
- [00-计算机组成原理](0203-计算机组成原理/00-计算机组成原理.md)
- [00-高等数学](0103-高等数学/00-高等数学.md)
- [数据结构与算法](0205-数据结构与算法/数据结构与算法.md)
- [00-大学语文](0101-语文/00-大学语文.md)
- [00-操作系统](0206-操作系统/00-操作系统.md)
- [00-英语](0102-英语/00-英语.md)

```dataviewjs
let file = dv.current()
let af = app.vault.getMarkdownFiles().filter(p=>p.path==file.file.path)[0]
let container = this.container

let content = await app.vault.readRaw(file.file.path)
let regexp = /(?<=\%\%)[\s\S]*?(?=\%\%)/
let rawText = regexp.exec(content)[0].split('\n').filter(p=>p.length!=0)
let Data = rawText.map(p=>p.split('+|+')).map(p=>[p[0],Number(p[1]),p[2]=Number(p[2])])

// 表格元素
let rank = (data,i)=>{
 let com = table.createEl('div')
    let title = Data[i][0]
    let plan = com.createEl('span',{'text':Data[i][1]+'/'+Data[i][2]})
    let progress = com.createEl('progress')
    changePro(progress,Data[i][1]/Data[i][2],com)
    progress.value = Data[i][1]
    progress.max = Data[i][2]

    let button = com.createEl('div',)
    let btn_p = button.createEl('button',{'text':'+'})
    let btn_s = button.createEl('button',{'text':'-'})
    btn_p.addEventListener('click',async (evt)=> {
        midifyData(i,'p')
        progress.value = Data[i][1]
        changePro(progress,Data[i][1]/Data[i][2],com)
        plan.innerHTML = Data[i][1]+'/'+Data[i][2]
    })
    btn_s.addEventListener('click',async (evt)=> {
        midifyData(i,'s')
        progress.value = Data[i][1]
        changePro(progress,Data[i][1]/Data[i][2],com)
        plan.innerHTML = Data[i][1]+'/'+Data[i][2]
    })
    return [title,plan,progress,button]
}

// 表格本体
let table = container.createEl("div");
let headers = ['标题','进度','进度条','修改']
let values = Data.map((p,i)=>rank(p,i))
createTable(headers,values,table)

// 保存按钮
let button_ = container.createEl('div',{'id':'con'})
let btn_save = button_.createEl('button',{'text':'save'})
btn_save.addEventListener('click',async (evt)=> {
    evt.preventDefault()
    let data = '\n'+Data.map(p=>p.join('+|+')).join('\n')+'\n'
    content = content.replace(regexp,data)
    app.vault.modify(af,content)
})

// 排序
let sortOptions = ['名称 A-Z','名称 Z-A','百分比-正序','百分比-倒序']
let sortFun = [
 (a,b)=>dv.compare(a[0],b[0]),
 (a,b)=>dv.compare(b[0],a[0]),
 (a,b)=>dv.compare(b[1]/b[2],a[1]/a[2]),
 (a,b)=>dv.compare(a[1]/a[2],b[1]/b[2]),
]
let se = button_.createEl('select')
let op = sortOptions.map(p=>se.createEl('option',{'text':p}))
se.onchange = function() {
 let index = se.selectedIndex
 table.empty()
 Data = Data.sort(sortFun[index])
    createTable(
     headers, 
     Data.map((p,i)=>rank(p,i)),
     table)
}

// 其他函数
function createTable(headers,values,t) {
 dv.table(headers,values)
 t.appendChild(container.getElementsByTagName('table')[0])
}
function changePro(progress, p, com) {
 if(p>=0 && p<0.3) progress.className = 'red'
 else if(p>=0.3 && p<0.6) progress.className = 'yellow'
 else if(p>=0.6 && p<1) progress.className = 'green'
 else if(p==1) progress.className = 'ok'

}
// 修改函数
function midifyData(i,m) {
    if(Data[i][1]<Data[i][2] && m=='p') Data[i][1] += 1
    if(Data[i][1]>0 && m=='s') Data[i][1] -= 1
}

```

%%
计算机基础 +|+3+|+8
操作系统 +|+2+|+5
大学语文 +|+15+|+25
高等数学 +|+12+|+12
计算机组成原理 +|+10+|+10
设计模式 +|+24+|+24
%%
